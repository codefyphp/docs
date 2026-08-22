---
title: PSR-15 middleware
sidebar_title: Middleware
weight: 9
---

# PSR-15 middleware

`Qubus\Http\RequestHandler` is a compact PSR-15 middleware dispatcher. It
accepts a PSR-17 response factory and an ordered list of middleware. When the
pipeline reaches its end, it returns a new 200 response from the factory.

## Building a pipeline

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

$requestId = new class implements MiddlewareInterface {
    public function process(
        ServerRequestInterface $request,
        RequestHandlerInterface $handler
    ): ResponseInterface {
        $id = bin2hex(random_bytes(8));
        $response = $handler->handle($request->withAttribute('request_id', $id));

        return $response->withHeader('X-Request-Id', $id);
    }
};

$endpoint = new class implements MiddlewareInterface {
    public function process(
        ServerRequestInterface $request,
        RequestHandlerInterface $handler
    ): ResponseInterface {
        return JsonResponseFactory::create([
            'request_id' => $request->getAttribute('request_id'),
        ]);
    }
};

$handler = new RequestHandler(new Psr17Factory(), [$requestId, $endpoint]);
$response = $handler->handle($request);
```

Middleware appears in request order and unwinds in reverse response order:

```text
request -> middleware A -> middleware B -> endpoint
response <- middleware A <- middleware B <- endpoint
```

!!!note
    The handler is reusable; handling one request does not consume the configured
    middleware list.

## Delegating middleware

Delegating middleware performs work before or after calling the next handler:

```php
<?php

final class SecurityHeaders implements MiddlewareInterface
{
    public function process(
        ServerRequestInterface $request,
        RequestHandlerInterface $handler
    ): ResponseInterface {
        return $handler->handle($request)
            ->withHeader('X-Content-Type-Options', 'nosniff')
            ->withHeader('Referrer-Policy', 'strict-origin-when-cross-origin');
    }
}
```

## Terminating middleware

A middleware may return a response without delegating:

```php
<?php

final class RequireApiKey implements MiddlewareInterface
{
    public function process(
        ServerRequestInterface $request,
        RequestHandlerInterface $handler
    ): ResponseInterface {
        if ($request->getHeaderLine('X-Api-Key') !== getenv('API_KEY')) {
            return JsonResponseFactory::create(
                ['error' => 'Unauthorized'],
                status: 401,
            );
        }

        return $handler->handle($request);
    }
}
```

## Recommended ordering

A typical outer-to-inner order is:

1. Error handling
2. Request IDs and access logging
3. Optional emitter middleware
4. Encrypted-cookie middleware
5. Session middleware
6. Authentication and authorization
7. Routing/controller dispatch

Ordering is application-specific. Cookie decryption must happen before code
reads those cookies; session middleware must happen before code reads the
session; response cookie encryption runs while the middleware stack unwinds.

If using `EmitterMiddleware`, keep it outside middleware that must still alter
the response. Alternatively, leave emission out of the pipeline and emit the
fully processed response in the front controller.

## Available middleware

| Middleware                                               | Purpose                                                                               |
|----------------------------------------------------------|---------------------------------------------------------------------------------------|
| `Qubus\Http\Cookies\Middleware\EncryptCookiesMiddleware` | Transparently decrypt incoming cookies and encrypt outgoing cookies.                  |
| `Qubus\Http\Session\Middleware\SessionMiddleware`        | Load a cache-backed session, attach it to the request, and commit it to the response. |
| `Qubus\Http\Emitter\Middleware\EmitterMiddleware`        | Emit the downstream response in a SAPI environment.                                   |

See [Cookies](cookies.md), [Sessions](sessions.md), and
[Responses](response.md) for complete configuration examples.
