---
title: Swoole Bridge
sidebar_title: Swoole
summary: Run Qubus PSR-7 and PSR-15 applications on Swoole with request conversion, streamed responses, worker-safe services, and error boundaries.
keywords: php-swoole,psr-15,swoole-server
weight: 14
---

!!!warning
    The current Swoole bridge is experimental and may not work as expected.

# Swoole Bridge

The Swoole bridge converts Swoole HTTP requests into PSR-7 server requests and
copies PSR-7 responses back to Swoole. It supports the `swoole` extension and
environments where OpenSwoole provides the compatible `Swoole\Http` classes.

## Requirements

Install one supported extension separately from Composer:

```shell
pecl install swoole
```

The bridge is optional; the rest of Qubus HTTP Component does not require Swoole.

Check your runtime:

```php
<?php

if (!extension_loaded('swoole') && !extension_loaded('openswoole')) {
    throw new RuntimeException('Swoole or OpenSwoole is required.');
}
```

## Minimal server

The `request_callback()` helper accepts either a callable or a PSR-15 request
handler:

```php
<?php

declare(strict_types=1);

use Psr\Http\Message\ServerRequestInterface;
use Qubus\Http\Factories\JsonResponseFactory;
use Swoole\Http\Server;

use function Qubus\Http\Swoole\Callback\Helpers\request_callback;

require dirname(__DIR__) . '/vendor/autoload.php';

$server = new Server('127.0.0.1', 9501);

$server->on('request', request_callback(
    static function (ServerRequestInterface $request) {
        return JsonResponseFactory::create([
            'method' => $request->getMethod(),
            'path' => $request->getUri()->getPath(),
            'query' => $request->getQueryParams(),
        ]);
    },
));

$server->start();
```

The callback maps request method, URI and query string, headers, cookies,
uploaded files, parsed POST data, and the raw request body. It then writes the
PSR response status, headers, and body before ending the Swoole response.

## Using a PSR-15 handler

```php
<?php

use Qubus\Http\Factories\Psr17Factory;
use Qubus\Http\RequestHandler;

$application = new RequestHandler(
    new Psr17Factory(),
    [$errorMiddleware, $sessionMiddleware, $routerMiddleware],
);

$server->on('request', request_callback($application));
```

Do not include `EmitterMiddleware` or call a SAPI emitter in this pipeline.
The Swoole callback owns response emission.

## Chunk size and stream factory

Large readable bodies are copied in chunks. Configure the size or provide
another PSR-17 stream factory:

```php
<?php

use Qubus\Http\Factories\Psr17Factory;
use Qubus\Http\Swoole\Callback\RequestCallbackOptions;

$options = RequestCallbackOptions::create()
    ->setResponseChunkSize(512 * 1024)
    ->setStreamFactory(new Psr17Factory());

$server->on('request', request_callback($application, $options));
```

Use a positive chunk size. The default is 2 MiB.

## Explicit request conversion

Frameworks that need direct access to the Swoole-aware PSR-7 implementation can
use `Qubus\Http\Swoole\Factory\RequestFactory`:

```php
<?php

use Qubus\Http\Factories\Psr17Factory;
use Qubus\Http\Swoole\Factory\RequestFactory;

$psr17 = new Psr17Factory();
$swooleFactory = new RequestFactory(
    uriFactory: $psr17,
    streamFactory: $psr17,
    uploadedFileFactory: $psr17,
);

$server->on('request', static function ($swooleRequest, $swooleResponse) use (
    $swooleFactory,
    $application
): void {
    $request = $swooleFactory->createServerRequest($swooleRequest);
    $response = $application->handle($request);

    new \Qubus\Http\Swoole\ResponseMerger()
        ->toSwoole($response, $swooleResponse);

    $swooleResponse->end();
});
```

The factory can also create a plain `RequestInterface`:

```php
<?php

$request = $swooleFactory->createRequest($swooleRequest);
```

The Swoole-backed request implementations follow PSR-7 immutability. Calling
`withHeader()`, `withMethod()`, `withUri()`, or a server-request `with*`
method returns a clone and does not mutate the original Swoole request.

## Accessing request data

Use standard PSR-7 APIs:

```php
<?php

$method = $request->getMethod();
$target = $request->getRequestTarget();
$uri = $request->getUri();
$headers = $request->getHeaders();
$body = (string) $request->getBody();

$server = $request->getServerParams();
$cookies = $request->getCookieParams();
$query = $request->getQueryParams();
$parsedBody = $request->getParsedBody();
$files = $request->getUploadedFiles();
```

Basic Authorization user info is included in the generated URI only when its
base64 value is valid. Avoid logging the full URI when it may contain user info.

## ResponseMerger behavior

`ResponseMerger`:

- copies the PSR status code;
- combines ordinary multi-value headers with commas;
- emits each `Set-Cookie` separately through Swoole's cookie API;
- uses `sendfile()` for eligible plain-file streams;
- reads pipe streams in bounded chunks; and
- writes other response bodies normally.

`toSwoole()` returns the Swoole response after copying content but does not call
`end()`. The explicit integration must end the response exactly once.

The higher-level `RequestCallback` handles completion for you.

## Long-running worker rules

Unlike PHP-FPM, a Swoole worker handles many requests in one process. Design
services and middleware accordingly:

- Do not store a request, response, user, session, or authorization result in a
  static property or shared singleton.
- Do not use `$_GET`, `$_POST`, `$_COOKIE`, or `$_SERVER` as request-local
  storage. Read the PSR request instead.
- Ensure mutable middleware is reset per request or keep middleware stateless.
- Close files, database cursors, and other resources deterministically.
- Do not call `header()`, `setcookie()`, or SAPI emitters.
- Load configuration and encryption keys at worker startup.
- Configure database/cache clients for reconnects and coroutine safety.

Qubus' Swoole server request reads directly from the supplied Swoole request and
does not copy request data into PHP superglobals.

## Error boundary

Install error-handling middleware that always returns a PSR response. Letting an
exception escape the request callback can leave a response unfinished and may
expose implementation details through server logs.

```php
<?php

try {
    $response = $application->handle($request);
} catch (Throwable $error) {
    $logger->error('Request failed', ['exception' => $error]);
    $response = JsonResponseFactory::create(
        ['error' => 'Internal Server Error'],
        status: 500,
    );
}
```

!!!note
    Log a generated request ID, not sensitive headers, cookies, or bodies.
