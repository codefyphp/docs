---
title: Qubus HTTP Component
sidebar_title: Introduction
weight: 0
---

The HTTP Component is a PHP 8.4+ toolkit for working with HTTP messages in applications,
frameworks, middleware stacks, and long-running Swoole servers. It builds on
Laminas Diactoros and implements the standard PHP HTTP interfaces:

- PSR-7 HTTP messages
- PSR-15 server middleware and request handlers
- PSR-17 HTTP factories

The package also provides URI and input helpers, response factories, SAPI
emitters, immutable cookie collections, encrypted cookies, native and
cache-backed sessions, flash messages, and a Swoole bridge.

## Installation

```shell
composer require qubus/http
```

```php
<?php

declare(strict_types=1);

require dirname(__DIR__) . '/vendor/autoload.php';
```

Swoole support is optional, yet experimental, and requires either `ext-swoole` or
`ext-openswoole`.

## Quick start

Create a PSR-7 server request, pass it through a PSR-15 handler, and produce a
JSON response:

```php
<?php

declare(strict_types=1);

use Psr\Http\Message\ResponseInterface;
use Psr\Http\Message\ServerRequestInterface;
use Psr\Http\Server\MiddlewareInterface;
use Psr\Http\Server\RequestHandlerInterface;
use Qubus\Http\Factories\JsonResponseFactory;
use Qubus\Http\Factories\Psr17Factory;
use Qubus\Http\RequestHandler;

$factory = new Psr17Factory();

$request = $factory
    ->createServerRequest('GET', 'https://example.com/api/health')
    ->withHeader('Accept', 'application/json');

$middleware = new class implements MiddlewareInterface {
    public function process(
        ServerRequestInterface $request,
        RequestHandlerInterface $handler
    ): ResponseInterface {
        return JsonResponseFactory::create([
            'ok' => true,
            'path' => $request->getUri()->getPath(),
        ]);
    }
};

$response = new RequestHandler($factory, [$middleware])->handle($request);
```

In a traditional PHP entry point, emit that response once all application work
has completed:

```php
<?php

use Qubus\Http\Emitter\SapiEmitter;

new SapiEmitter()->emit($response);
```

## Choosing the right request type

| Type                              | Use it when                                                                                                 |
|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
| `Qubus\Http\Request`              | You want a client-style PSR-7 request plus convenient access to PHP globals and parsed input.               |
| `Qubus\Http\ServerRequest`        | You want a standard PSR-7 server request with attributes, cookies, uploaded files, and parsed-body APIs.    |
| `Qubus\Http\Swoole\ServerRequest` | A Swoole worker supplies the incoming request. Normally create this through the Swoole factory or callback. |

For framework internals, prefer type-hinting PSR interfaces. Use concrete Qubus
types only when you need their additional helpers:

```php
<?php

use Psr\Http\Message\ServerRequestInterface;

function controller(ServerRequestInterface $request): array
{
    return [
        'method' => $request->getMethod(),
        'path' => $request->getUri()->getPath(),
        'query' => $request->getQueryParams(),
    ];
}
```

## Immutability

PSR-7 messages, `Url`, `Cookies`, `CookieCollection`, `SetCookies`, and
`SetCookieCollection` are immutable. Methods named `with*` and `without*`
return a changed copy; they do not modify the original object.

```php
<?php

$jsonResponse = $response
    ->withStatus(201)
    ->withHeader('Content-Type', 'application/json');

// $response still has its original status and headers.
```

The input helper and native session classes are stateful. Their setter methods
operate on the current instance.

## More Info and Documentation

- [Requests and Input](request.md)
- [Responses, Factories, and Emitters](response.md)
- [PSR-15 Middleware](middleware.md)
- [Cookies](cookies.md)
- [Sessions and Flash Messages](sessions.md)
- [Encryption](encryption.md)
- [Swoole Bridge](swoole.md)

## Security defaults

The HTTP Component validates cookie names and attributes before rendering them, requires
secure transport for `SameSite=None`, `Partitioned`, and secure cookie prefixes,
uses authenticated encryption through Defuse PHP Encryption, and escapes flash
message HTML by default.

Applications remain responsible for deployment-level trust decisions:

- Pass `true` to forwarded-header helpers only behind a trusted reverse proxy.
- Use HTTPS for authentication and sensitive cookies.
- Generate encryption and signing keys with cryptographically secure tools; do
  not place keys in source control.
- Validate and authorize all request input. Parsing input does not make it safe.
- Treat uploaded filenames and client MIME types as untrusted metadata.

