---
title: Cookies
sidebar_title: Cookies
summary: Read and create secure PSR-7 HTTP cookies with CodefyPHP, including SameSite settings, prefixes, partitioning, encryption, signing, and middleware.
keywords: php-cookies,psr-7,cookie-security
weight: 11
---

# Cookies

HTTP can request `Cookie` headers and response `Set-Cookie` headers as
immutable value objects. The collection APIs work with any PSR-7 request or
response implementation.

## Request cookies

A request cookie contains a name and value:

```php
<?php

use Qubus\Http\Cookies\CookieCollection;

$theme = CookieCollection::create('theme', 'dark');
$lightTheme = $theme->withValue('light');

$theme->getName();  // theme
$theme->getValue(); // dark
(string) $theme;    // theme=dark
```

Parse and inspect all request cookies:

```php
<?php

use Qubus\Http\Cookies\Cookies;

$cookies = Cookies::fromRequest($request);

if ($cookies->has('theme')) {
    $theme = $cookies->get('theme')?->getValue();
}

foreach ($cookies->getAll() as $cookie) {
    // $cookie is a CookieCollection value object.
}
```

Collections are immutable. Render the changed collection back into a request:

```php
<?php

$request = $cookies
    ->with(CookieCollection::create('locale', 'en-US'))
    ->without('legacy')
    ->renderIntoCookieHeader($request);
```

The facade offers concise get/set/modify/remove operations:

```php
<?php

use Qubus\Http\Cookies\CookiesRequest;

$locale = CookiesRequest::get($request, 'locale', 'en-US')->getValue();

$request = CookiesRequest::set(
    $request,
    CookieCollection::create('theme', 'dark'),
);

$request = CookiesRequest::modify(
    $request,
    'visit_count',
    static fn (CookieCollection $cookie): CookieCollection =>
        $cookie->withValue((string) ((int) $cookie->getValue() + 1)),
);

$request = CookiesRequest::remove($request, 'legacy');
```

Removing a request header value only changes the server-side request object. To
tell a browser to remove stored state, expire a response cookie with the same
name, path, and domain as the original cookie.

## Response cookies

Build a `Set-Cookie` value with explicit security attributes:

```php
<?php

use Qubus\Http\Cookies\CookiesResponse;
use Qubus\Http\Cookies\SameSite;
use Qubus\Http\Cookies\SetCookieCollection;

$cookie = SetCookieCollection::create('__Host-session', 'opaque-value')
    ->withPath('/')
    ->withSecure()
    ->withHttpOnly()
    ->withSameSite(SameSite::lax())
    ->withMaxAge(3600)
    ->withExpires(time() + 3600);

$response = CookiesResponse::set($response, $cookie);
```

`Max-Age` is measured in seconds. Supplying both `Max-Age` and `Expires` is
useful for clients with differing support. `rememberForever()` sets an expiry
five years ahead; `expire()` sets one five years in the past.

```php
<?php

$persistent = SetCookieCollection::createRememberedForever('preferences', 'compact')
    ->withPath('/')
    ->withSecure()
    ->withHttpOnly()
    ->withSameSite(SameSite::lax());

$expired = $persistent->expire()->withMaxAge(0);
```

Use the response facade for common operations:

```php
<?php

$cookie = CookiesResponse::get($response, 'preferences', 'default');
$response = CookiesResponse::set($response, $persistent);

$response = CookiesResponse::modify(
    $response,
    'preferences',
    static fn (SetCookieCollection $cookie): SetCookieCollection =>
        $cookie->withValue('comfortable'),
);

$response = CookiesResponse::expire($response, 'preferences');
$response = CookiesResponse::remove($response, 'debug');
```

`remove()` removes a `Set-Cookie` header from the in-memory response.
`expire()` adds an expired cookie that instructs the client to delete stored
state. For a non-default path or domain, configure the same attributes on an
expired `SetCookieCollection` and pass it to `set()`.

## Multiple Set-Cookie headers

Each response cookie must be its own header field. `SetCookies` preserves that
representation:

```php
<?php

use Qubus\Http\Cookies\SetCookies;

$setCookies = SetCookies::fromResponse($response)
    ->with($persistent)
    ->with(
        SetCookieCollection::create('consent', 'yes')
            ->withPath('/')
            ->withSecure()
            ->withSameSite(SameSite::strict()),
    );

$response = $setCookies->renderIntoSetCookieHeader($response);
```

Existing header strings can be parsed:

```php
<?php

$cookie = SetCookieCollection::fromSetCookieString(
    'theme=dark; Path=/; Secure; HttpOnly; SameSite=Lax',
);
```

## SameSite, prefixes, and partitioning

Supported SameSite values are created explicitly:

```php
<?php

SameSite::strict();
SameSite::lax();
SameSite::none();
SameSite::fromString('LAX');
```

Security rules are enforced when the cookie is rendered:

| Feature                 | Required attributes                 |
|-------------------------|-------------------------------------|
| `SameSite=None`         | `Secure`                            |
| `Partitioned`           | `Secure`                            |
| `__Secure-` name prefix | `Secure`                            |
| `__Host-` name prefix   | `Secure`, `Path=/`, and no `Domain` |

Create a partitioned third-party cookie:

```php
<?php

$partitioned = SetCookieCollection::create('__Host-widget', 'state')
    ->withPath('/')
    ->withSecure()
    ->withHttpOnly()
    ->withSameSite(SameSite::none())
    ->withPartitioned();
```

Invalid names and path/domain values containing control characters or
semicolon delimiters are rejected to prevent response-header injection.

## CookieFactory

`CookieFactory` reads common defaults from a `ConfigContainer`. Recognized keys
are `cookies.path`, `cookies.domain`, `cookies.secure`,
`cookies.samesite`, and `cookies.lifetime` (the latter is also used by
`SessionService`).

```php
<?php

use Qubus\Config\Collection;
use Qubus\Http\Cookies\Factory\CookieFactory;

$config = Collection::factory(['path' => '/srv/app/config']);
$factory = new CookieFactory($config);

$cookie = $factory->make('cart', 'cart-id', maxAge: 3600);
$response = CookiesResponse::set($response, $cookie);
```

A typical cookies configuration file returns:

```php
<?php

return [
    'path' => '/',
    'domain' => '',
    'secure' => true,
    'samesite' => 'lax',
    'lifetime' => 3600,
];
```

The precise file layout is controlled by `qubus/config`. You can instead
implement `HttpCookieFactory` to connect session cookies to another
configuration system.

## Transparent cookie encryption middleware

For a middleware-wide policy, load a Defuse key and configure names that must
remain readable by other systems:

```php
<?php

use Defuse\Crypto\Key;
use Qubus\Http\Cookies\Middleware\EncryptCookiesMiddleware;

$key = Key::loadFromAsciiSafeString((string) getenv('COOKIE_ENCRYPTION_KEY'));

$middleware = new EncryptCookiesMiddleware(
    cryptoKey: $key,
    bypassCookieNames: ['consent', 'locale'],
);
```

The middleware decrypts non-bypassed incoming cookies before delegating and
encrypts non-bypassed response cookies while unwinding. A cookie that cannot be
decrypted is replaced with an empty value rather than exposing error details.

Install it before middleware that consumes cookies:

```php
<?php

$handler = new \Qubus\Http\RequestHandler(
    $psr17Factory,
    [$middleware, $sessionMiddleware, $applicationMiddleware],
);
```

## Explicit encrypt-and-sign helpers

When only selected cookies need protection, combine an `Encryption` adapter
with HMAC validation:

```php
<?php

use Defuse\Crypto\Key;
use Qubus\Http\Cookies\RequestCookieDecryptor;
use Qubus\Http\Cookies\ResponseCookieEncryptor;
use Qubus\Http\Cookies\Validation\Validation;
use Qubus\Http\Encryption\Adapter\QubusEncryption;

$encryption = new QubusEncryption(
    Key::loadFromAsciiSafeString((string) getenv('COOKIE_ENCRYPTION_KEY')),
);
$validation = new Validation(
    key: (string) getenv('COOKIE_SIGNING_KEY'),
    algo: 'sha256',
);

$outgoing = new ResponseCookieEncryptor($encryption, $validation);
$response = $outgoing->encrypt($response, ['cart', 'preferences']);

$incoming = new RequestCookieDecryptor($encryption, $validation);
$request = $incoming->decrypt($request, ['cart', 'preferences']);
```

This format encrypts, signs, and base64-encodes values. Tampering, malformed
base64, or a mismatched signing key raises an exception. Handle that exception
at the request boundary by rejecting or expiring the invalid cookie.

Keep encryption and signing keys distinct, random, outside source control, and
stable across all application instances that must share cookies.

## Cookie security checklist

- Use `Secure` and HTTPS for any sensitive state.
- Use `HttpOnly` unless browser JavaScript genuinely requires access.
- Prefer `SameSite=Lax` or `Strict`; use `None` only for intentional
  cross-site behavior.
- Keep the narrowest practical `Path` and omit `Domain` for host-only cookies.
- Store opaque identifiers rather than credentials or large serialized data.
- Expire cookies with the exact path/domain used when creating them.
- Encryption provides confidentiality, not authorization. Validate decrypted
  data and enforce server-side permissions.
