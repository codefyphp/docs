---
title: Sessions and flash messages
sidebar_title: Sessions
summary: Manage secure PHP sessions and flash messages with native or cache-backed storage, typed values, PSR-7 lifecycles, and session middleware.
keywords: php-sessions,flash-messages,session-middleware
weight: 12
---

# Sessions and flash messages

The package supports two different session models:

| Model                              | Best for                                                                        |
|------------------------------------|---------------------------------------------------------------------------------|
| `NativeSession`                    | Conventional PHP applications using `$_SESSION` and a PHP session save handler. |
| `SessionService` and `HttpSession` | PSR-7/PSR-15 applications storing typed session entities in a PSR-16 cache.     |

Choose one model for a given application flow. The APIs represent different
storage approaches and are not interchangeable.

## Native PHP sessions

`NativeSession` wraps PHP's native session functions and accepts a Qubus
`ConfigContainer` plus an optional `SessionHandlerInterface`.

```php
<?php

declare(strict_types=1);

use Qubus\Config\Collection;
use Qubus\Http\Session\NativeSession;

$config = Collection::factory(['path' => '/srv/app/config']);
$session = new NativeSession($config);

$session->set('user_id', '0192f32a-39a7-7bd8-9ab1-8fbd431a9e62');
$userId = $session->get('user_id');

if ($session->has('checkout')) {
    $checkout = $session->get('checkout');
}

$all = $session->getAll();
$session->unsetSession('temporary');
```

Sessions start lazily when data is accessed. You may also control the lifecycle:

```php
<?php

$session->startSession();
$id = $session->sessionId();
$name = $session->currentSessionName();

// Renew after privilege changes such as a successful login.
$session->regenerateId();

// Remove application values but keep the active session.
$session->clear();

// Destroy the native PHP session.
$session->destroySession();
```

## Native session configuration

The `session` configuration section is merged with secure defaults:

| Option             |   Default | Meaning                                                 |
|--------------------|----------:|---------------------------------------------------------|
| `use_cookies`      |       `1` | Transport the ID in a cookie.                           |
| `cookie_secure`    |       `1` | Send the cookie only over HTTPS.                        |
| `cookie_lifetime`  |     `360` | Cookie lifetime in seconds; zero means browser session. |
| `cookie_path`      |       `/` | Cookie path.                                            |
| `cookie_domain`    |     empty | Cookie domain; empty produces a host-only cookie.       |
| `use_only_cookies` |       `1` | Do not accept IDs through URLs.                         |
| `cookie_httponly`  |       `1` | Prevent JavaScript access.                              |
| `use_strict_mode`  |       `1` | Reject uninitialized IDs supplied by clients.           |
| `cache_limiter`    | `nocache` | PHP session cache limiter.                              |
| `cache_expire`     |     `180` | Cache expiry in minutes where applicable.               |
| `cookie_samesite`  |     `Lax` | SameSite cookie policy.                                 |

Example configuration:

```php
<?php

return [
    'use_cookies' => true,
    'cookie_secure' => true,
    'cookie_lifetime' => 3600,
    'cookie_path' => '/',
    'cookie_domain' => '',
    'use_only_cookies' => true,
    'cookie_httponly' => true,
    'use_strict_mode' => true,
    'cache_limiter' => 'nocache',
    'cache_expire' => 180,
    'cookie_samesite' => 'Lax',
];
```

PHP session configuration must be applied before output is sent. In long-running
workers, avoid native process-global sessions and use the cache-backed model.

## Flash messages

`Flash` stores messages through a writable `PhpSession` implementation such as
`NativeSession`. Message output is escaped by default.

```php
<?php

use Qubus\Http\Session\Flash;
use Qubus\Http\Session\MessageType;

$flash = new Flash($session);

$flash->info('Your profile is available.');
$flash->success('Your changes were saved.');
$flash->warning('Your session will expire soon.');
$flash->error('The payment could not be processed.');
$flash->sticky('Maintenance begins at 22:00.', type: MessageType::WARNING);

if ($flash->hasErrors()) {
    // Show an error summary or alter the response status.
}
```

Render all queued messages and consume them:

```php
<?php

$html = $flash->display(print: false);

if ($html !== false) {
    $response->getBody()->write($html);
}
```

Render selected message types:

```php
<?php

use Qubus\Http\Session\MessageType;

$errors = $flash->display(MessageType::ERROR, print: false);
$notices = $flash->display(
    [MessageType::INFO, MessageType::WARNING],
    print: false,
);

$flash->hasMessages();
$flash->hasMessages(MessageType::SUCCESS);
```

Customize the generated markup:

```php
<?php

$flash
    ->setMsgWrapper('<aside class="%s">%s</aside>')
    ->setMsgBefore('<span class="icon" aria-hidden="true"></span>')
    ->setMsgAfter('')
    ->setCloseBtn('<button type="button" aria-label="Dismiss">×</button>')
    ->setMsgCssClass('notice')
    ->setStickyCssClass('notice--sticky')
    ->setCssClassMap([
        MessageType::INFO => 'notice--info',
        MessageType::SUCCESS => 'notice--success',
        MessageType::WARNING => 'notice--warning',
        MessageType::ERROR => 'notice--error',
    ]);
```

Only call `setEscapeHtml(false)` when every message is trusted application-owned
HTML. Never disable escaping for validation messages or other user-controlled
content.

## Cache-backed typed sessions

The PSR-7 session model stores small typed objects rather than a global
key/value array. Define a zero-argument entity implementing `SessionEntity`:

```php
<?php

declare(strict_types=1);

namespace App\Session;

use Qubus\Http\Session\SessionEntity;

final class UserSession implements SessionEntity
{
    private ?string $userId = null;

    public function userId(): ?string
    {
        return $this->userId;
    }

    public function authenticate(string $userId): void
    {
        $this->userId = $userId;
    }

    public function clear(): void
    {
        $this->userId = null;
    }

    public function isEmpty(): bool
    {
        return $this->userId === null;
    }
}
```

Entity requirements:

- The class must exist and have a constructor that needs no arguments.
- State must be serializable by Qubus' JSON serializer.
- `isEmpty()` must return true for the entity's default/cleared state.
- Keep entities focused on one domain rather than building a catch-all bag.
- Changing the entity source invalidates its previously serialized form, so
  deploy schema changes with the expectation that this entity may reset.

## Storage and service setup

Adapt any PSR-16 cache with `SimpleCacheStorage`:

```php
<?php

use Qubus\Http\Cookies\Factory\CookieFactory;
use Qubus\Http\Session\SessionService;
use Qubus\Http\Session\Storage\SimpleCacheStorage;

// $cache implements Psr\SimpleCache\CacheInterface.
$storage = new SimpleCacheStorage($cache);
$cookieFactory = new CookieFactory($config);
$sessions = new SessionService($storage, $cookieFactory);

SessionService::$options = [
    'cookie-name' => 'QSESSID',
    'cookie-lifetime' => 3600,
];
```

The cache key is a one-way derived server session ID. The client receives a
UUID cookie, not the cache key itself.

For another backend, implement the three-method storage interface:

```php
<?php

use Qubus\Http\Session\Storage\SessionStorage;

final class DatabaseSessionStorage implements SessionStorage
{
    public function read(string $sessionId): ?array
    {
        // Return decoded session data, or null when absent.
    }

    public function write(string $sessionId, array $data, int $ttl): void
    {
        // Upsert data with an expiry.
    }

    public function destroy(string $sessionId): void
    {
        // Delete the record.
    }
}
```

Storage implementations should treat TTL as seconds, make writes atomic, and
avoid logging IDs or serialized session contents.

## Manual PSR-7 lifecycle

Load from request cookies, mutate an entity, and commit into the response:

```php
<?php

use App\Session\UserSession;
use Qubus\Http\Factories\JsonResponseFactory;

$session = $sessions->makeSession($request);

/** @var UserSession $user */
$user = $session->get(UserSession::class);
$user->authenticate('user-42');

$response = JsonResponseFactory::create(['authenticated' => true]);
$response = $sessions->commitSession($response, $session);
```

Commit after all session changes. Empty sessions are not stored. If a
previously stored session becomes empty, its server record is destroyed and its
cookie is expired.

Renew the ID after authentication while keeping current state:

```php
<?php

$session->renew();
$response = $sessions->commitSession($response, $session);
```

Clear all state on logout:

```php
<?php

$session->clear();
$response = $sessions->commitSession($response, $session);
```

`clear()` orphans previously retrieved entity objects; changes made to those old
references afterward are not committed.

## Session middleware

Middleware automates loading and committing:

```php
<?php

use App\Session\UserSession;
use Psr\Http\Message\ResponseInterface;
use Psr\Http\Message\ServerRequestInterface;
use Psr\Http\Server\MiddlewareInterface;
use Psr\Http\Server\RequestHandlerInterface;
use Qubus\Http\Session\HttpSession;
use Qubus\Http\Session\Middleware\SessionMiddleware;

$sessionMiddleware = new SessionMiddleware($sessions);

$application = new class implements MiddlewareInterface {
    public function process(
        ServerRequestInterface $request,
        RequestHandlerInterface $handler
    ): ResponseInterface {
        $session = $request->getAttribute(
            SessionMiddleware::SESSION_OBJECT_ATTRIBUTE,
        );

        if (!$session instanceof HttpSession) {
            throw new \RuntimeException('Session middleware is required.');
        }

        /** @var UserSession $user */
        $user = $session->get(UserSession::class);

        return $handler->handle(
            $request->withAttribute('current_user_id', $user->userId()),
        );
    }
};
```

The middleware exposes two attributes:

| Constant                   | Value                                           |
|----------------------------|-------------------------------------------------|
| `SESSION_OBJECT_ATTRIBUTE` | The `HttpSession` object; use this in new code. |
| `SESSION_ATTRIBUTE`        | The client session ID string.                   |

The client session ID is deliberately not copied into an HTTP header.

## Session security

- Renew the cache-backed session with `renew()`, or native session with
  `regenerateId()`, immediately after successful authentication or a privilege
  elevation.
- Clear/destroy sessions during logout.
- Configure `Secure`, `HttpOnly`, host-only scope, and an appropriate SameSite
  policy for the session cookie.
- Keep authentication and authorization decisions server-side.
- Use a shared cache for multi-instance deployments and configure eviction/TTL
  consistently.
- Do not place secrets, large payloads, open resources, or service objects in
  session entities.
