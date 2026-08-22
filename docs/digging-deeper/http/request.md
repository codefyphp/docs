---
title: Requests and input
sidebar_title: Requests
summary: Create and inspect PSR-7 server requests with Qubus HTTP, including URIs, headers, client addresses, authentication, parsed input, files, and negotiation.
keywords: psr-7-request,http-input,php-request
weight: 7
---

# Requests and input

The HTTP Component provides PSR-7 request implementations for both generic requests and
server-side requests. All standard PSR-7 methods are available, including
`getMethod()`, `getUri()`, `getHeaders()`, `getBody()`, and their immutable
`with*` counterparts.

## Creating requests

Use `Request` when its global/input convenience helpers are useful:

```php
<?php

declare(strict_types=1);

use Qubus\Http\Request;

$request = new Request(
    uri: 'https://api.example.com/search?q=http&page=2',
    method: 'GET',
    headers: [
        'Accept' => 'application/json',
        'User-Agent' => 'ExampleClient/1.0',
    ],
);
```

When the URI or method is omitted, `Request` derives it from `$_SERVER`.
Applications that construct requests explicitly should provide both values to
avoid coupling the result to process globals.

Use the PSR-17 factory when framework code should depend on standard factory
interfaces:

```php
<?php

use Psr\Http\Message\RequestFactoryInterface;
use Psr\Http\Message\ServerRequestFactoryInterface;
use Qubus\Http\Factories\Psr17Factory;

$factory = new Psr17Factory();

assert($factory instanceof RequestFactoryInterface);
assert($factory instanceof ServerRequestFactoryInterface);

$request = $factory->createRequest('POST', 'https://example.com/orders');
$serverRequest = $factory->createServerRequest(
    'GET',
    'https://example.com/users/42',
    ['REMOTE_ADDR' => '203.0.113.10'],
);
```

`ServerRequest` accepts the complete PSR-7 server-request state in its
constructor and adds a small `get()` shortcut for array parsed bodies:

```php
<?php

use Qubus\Http\ServerRequest;

$request = new ServerRequest(
    serverParams: ['REMOTE_ADDR' => '203.0.113.10'],
    uri: 'https://example.com/profile',
    method: 'POST',
    headers: ['Content-Type' => 'application/json'],
    cookies: ['theme' => 'dark'],
    queryParams: ['preview' => '1'],
    parsedBody: ['display_name' => 'Ada'],
);

$name = $request->get('display_name', 'Anonymous');
```

Use `ServerRequestFactory::fromGlobals()` when you need Diactoros' standard
conversion from PHP superglobals:

```php
<?php

use Qubus\Http\ServerRequestFactory;

$request = ServerRequestFactory::fromGlobals();
```

## Working with PSR-7 requests

Every operation that changes PSR-7 state returns a new request:

```php
<?php

$authenticated = $request
    ->withMethod('PUT')
    ->withHeader('Authorization', 'Bearer example-token')
    ->withAttribute('user_id', 42);
```

Attributes are application metadata. Headers are HTTP protocol data. Keep
authenticated identities, route results, and service objects in attributes
rather than inventing transport headers.

## URI helpers

`Url` implements `UriInterface` and adds query, relative/absolute URL, and
inspection helpers:

```php
<?php

use Qubus\Http\Url;

$url = new Url('https://alice:secret@example.com:8443/items?sort=name&page=2#results');

$url->getScheme();       // https
$url->getAuthority();    // alice:secret@example.com:8443
$url->getHost();         // example.com
$url->getPort();         // 8443
$url->getPath();         // /items
$url->getParams();       // ['sort' => 'name', 'page' => '2']
$url->getParam('page');  // '2'
$url->getFragment();     // results
$url->getRelativeUrl();  // /items?sort=name&page=2#results
$url->getAbsoluteUrl();  // full URL
$url->isSecure();        // true
$url->isRelative();      // false
```

URI mutations are immutable:

```php
<?php

$pageThree = $url
    ->mergeParams(['page' => 3, 'filter' => 'active'])
    ->removeParam('sort')
    ->withFragment('top');

$withoutQuery = $pageThree->withParams([]);
$pathOnly = $pageThree->getRelativeUrl(includeParams: false);
```

`withParams()` replaces the query; `mergeParams()` overlays new values;
`removeParam()` and `removeParams()` delete selected keys. Nested arrays use
PHP's normal `http_build_query()` representation.

```php
<?php

$query = Url::arrayToParams([
    'filter' => ['status' => 'open'],
    'page' => 1,
]);
// filter%5Bstatus%5D=open&page=1
```

`getOriginalUrl()` and `getOriginalPath()` describe the string supplied to the
constructor. They intentionally do not change after immutable URI mutations.

## Convenience request metadata

The concrete `Request` exposes normalized accessors:

```php
<?php

$request->getHost();
$request->getScheme();
$request->getContentType();
$request->getUserAgent();
$request->getReferer();
$request->getServerName();
$request->getServerAddress();
$request->getServer('remote-addr');
$request->hasServer('http-authorization');
```

Server names are normalized to lowercase with underscores replaced by hyphens,
so `HTTP_USER_AGENT` is available as `http-user-agent`.

Common request checks include:

```php
<?php

if ($request->isPost() && $request->isAjax()) {
    // Handle an XMLHttpRequest POST.
}

$request->isGet();
$request->isPut();
$request->isPatch();
$request->isDelete();
$request->isHead();
$request->isOptions();
$request->isConnect();
$request->isTrace();
$request->isPostBack(); // POST, PUT, PATCH, or DELETE
```

For HTML forms, a POST field named `_method` can override the request method to
another supported method:

```html
<input type="hidden" name="_method" value="PATCH">
```

!!!note
    Only an actual POST request is eligible for the override.

## Client addresses and proxies

By default, use the connection address because forwarded headers are supplied
by clients and can be spoofed:

```php
<?php

$address = $request->getClientAddress();
$secure = $request->isSecure();
```

Trust forwarded headers only after your web server has removed untrusted values
and only when the application is reachable through a trusted proxy:

```php
<?php

$address = $request->getClientAddress(trustForwardedHeader: true);
$secure = $request->isSecure(trustForwardedHeader: true);
```

`getIp(safeMode: true)` similarly limits lookup to `REMOTE_ADDR`. The default
legacy behavior also considers common forwarding headers; security-sensitive
applications should use safe mode unless the proxy boundary is controlled.

## Authentication headers

```php
<?php

$basic = $request->getBasicAuth();
if ($basic !== null) {
    $username = $basic['username'];
    $password = $basic['password'];
}

$digestFields = $request->getDigestAuth();
```

These helpers parse credentials; they do not authenticate or authorize them.
Avoid logging credentials or complete authorization headers.

## Parsed input

`Request::handler()` combines query parameters, form fields, JSON bodies, and
PHP upload data. It recognizes JSON from `Content-Type: application/json` and
also accepts JSON object/array bodies for compatibility.

```php
<?php

use Qubus\Http\Factories\Psr17Factory;
use Qubus\Http\Request;

$body = new Psr17Factory()->createStream(
    '{"name":"Ada","roles":["editor"]}',
);
$request = new Request(
    uri: 'https://example.com/search?page=2',
    method: 'POST',
    body: $body,
    headers: ['Content-Type' => 'application/json; charset=utf-8'],
);

$input = $request->handler();

$page = $input->value('page', 1, Request::REQUEST_TYPE_GET);
$name = $input->value('name', 'Anonymous', Request::REQUEST_TYPE_POST);
$roles = $input->value('roles', [], Request::REQUEST_TYPE_POST);
```

The main operations are:

| Method                               | Result                                                     |
|--------------------------------------|------------------------------------------------------------|
| `get($key, $default)`                | Query `Input`, nested input array, or default.             |
| `post($key, $default)`               | Body `Input`, nested input array, or default.              |
| `file($key, $default)`               | Uploaded `File`, nested upload array, or default.          |
| `find($key, ...$methods)`            | Search selected sources or query/body/files in that order. |
| `value($key, $default, ...$methods)` | Return an unwrapped scalar/array value.                    |
| `exists($keyOrKeys, ...$methods)`    | Test one key or require every supplied key.                |
| `all($filter)`                       | Return raw merged input, optionally limited to named keys. |

```php
<?php

if ($input->exists(['email', 'password'], Request::REQUEST_TYPE_POST)) {
    $credentials = $input->all(['email', 'password']);
}

$item = $input->post('email');
if ($item instanceof \Qubus\Http\Input\Input) {
    $label = $item->getName();
    $value = $item->getValue();
}
```

`Input` implements `ArrayAccess`, `IteratorAggregate`, and string conversion,
which is useful for nested form fields. Prefer `value()` when you need plain
application data.

## Uploaded files

The legacy input handler wraps `$_FILES` entries in `Qubus\Http\Input\File`:

```php
<?php

use Qubus\Http\Input\File;

$upload = $request->handler()->file('avatar');

if ($upload instanceof File && !$upload->hasError()) {
    $clientFilename = $upload->getFilename();
    $clientMime = $upload->getType();
    $size = $upload->getSize();
    $contents = $upload->getContents();
    $upload->move('/srv/app/uploads/generated-safe-name.bin');
}
```

The filename and MIME type originate from the client. Generate destination
names yourself, enforce size limits, and inspect file contents with a trusted
server-side mechanism before accepting an upload. For portable framework code,
prefer the PSR-7 `getUploadedFiles()` API on `ServerRequestInterface`.

## Content negotiation

```php
<?php

if ($request->isFormatAccepted('application/json')) {
    // JSON is present in Accept.
}

$formats = $request->getAcceptFormats();
```

These are convenient substring/list helpers rather than a full RFC quality and
specificity negotiator. Applications requiring weighted negotiation should use
a dedicated negotiator.
