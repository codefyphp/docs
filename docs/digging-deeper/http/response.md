---
title: Responses, factories, and emitters
sidebar_title: Responses
weight: 8
---

# Responses, factories, and emitters

`Qubus\Http\Response` is a PSR-7 response based on Laminas Diactoros.
Responses are immutable: retain the object returned by every `with*` or
`without*` operation.

## Creating a response

```php
<?php

declare(strict_types=1);

use Qubus\Http\Factories\Psr17Factory;
use Qubus\Http\Response;

$response = new Response(
    body: new Psr17Factory()->createStream('Created'),
    status: 201,
    headers: ['Content-Type' => 'text/plain; charset=utf-8'],
);

$response = $response
    ->withHeader('X-Request-Id', 'req-123')
    ->withAddedHeader('Vary', 'Accept-Encoding');
```

The body may be a stream resource, a `StreamInterface`, or a stream URI such as
`php://memory`. A plain string passed directly to the constructor is interpreted
as a stream URI, so create a stream or use a specialized response factory for
literal content.

## Specialized response factories

```php
<?php

use Qubus\Http\Factories\EmptyResponseFactory;
use Qubus\Http\Factories\HtmlResponseFactory;
use Qubus\Http\Factories\JsonResponseFactory;
use Qubus\Http\Factories\RedirectResponseFactory;
use Qubus\Http\Factories\TextResponseFactory;
use Qubus\Http\Factories\XmlResponseFactory;

$html = HtmlResponseFactory::create(
    '<h1>Welcome</h1>',
    status: 200,
    headers: ['Cache-Control' => 'no-store'],
);

$json = JsonResponseFactory::create(['data' => ['id' => 42]]);

$problem = JsonResponseFactory::create(
    [
        'type' => 'https://example.com/problems/validation',
        'title' => 'Validation failed',
        'status' => 422,
        'errors' => ['email' => ['A valid email address is required.']],
    ],
    status: 422,
    headers: ['Content-Type' => 'application/problem+json'],
);

$text = TextResponseFactory::create('Accepted', status: 202);
$xml = XmlResponseFactory::create('<status>ok</status>');
$empty = EmptyResponseFactory::create(status: 204);
$redirect = RedirectResponseFactory::create('/login', status: 303);
```

`JsonResponseFactory::create()` accepts a fourth `encodingOptions` argument.
Its default follows Diactoros. Pass explicit JSON flags when your API contract
requires different escaping or formatting.

## PSR-17 factory

`Psr17Factory` implements request, server-request, response, stream,
uploaded-file, and URI factory interfaces:

```php
<?php

use Qubus\Http\Factories\Psr17Factory;

$factory = new Psr17Factory();

$response = $factory->createResponse(202, 'Queued');
$stream = $factory->createStream('response body');
$response = $response->withBody($stream);

$fileStream = $factory->createStreamFromFile('/srv/app/report.csv', 'rb');
$uri = $factory->createUri('https://example.com/reports/weekly');
```

Create an uploaded-file object from a stream:

```php
<?php

use const UPLOAD_ERR_OK;

$upload = $factory->createUploadedFile(
    stream: $fileStream,
    size: $fileStream->getSize(),
    error: UPLOAD_ERR_OK,
    clientFilename: 'report.csv',
    clientMediaType: 'text/csv',
);
```

`createStream()` treats its argument as content. Use
`createStreamFromFile()` when the argument is a filename.

## Status helpers

`Status` defines constants and reason phrases for standard and commonly used
extension status codes:

```php
<?php

use Qubus\Http\Status;

$response = $factory->createResponse(Status::CREATED);

Status::getMessageForCode(404);       // Not Found
Status::getMessageForCode(799);       // empty string
Status::isInformational(103);         // true
Status::isSuccessful(204);            // true
Status::isRedirect(308);              // true
Status::isClientError(422);           // true
Status::isServerError(503);           // true
Status::isError($response->getStatusCode());
```

Use the semantic helper matching your intent. Redirect classification covers
the complete `300..399` range; `isError()` covers `400..599`.

## Emitting a response under PHP-FPM or mod_php

Emit exactly once, after middleware and controllers have finished:

```php
<?php

use Qubus\Http\Emitter\SapiEmitter;

new SapiEmitter()->emit($response);
```

The emitter writes the status line, headers, and body, and detects output sent
before the response. Informational responses and statuses 204, 205, and 304 do
not emit a message body.

Headers cannot be emitted after application output. Keep entry points free of
byte-order marks, debugging output, and whitespace before `<?php`.

## Streaming large responses

`SapiStreamEmitter` reads the body in bounded chunks:

```php
<?php

use Qubus\Http\Emitter\SapiStreamEmitter;
use Qubus\Http\Factories\Psr17Factory;
use Qubus\Http\Response;

$factory = new Psr17Factory();
$response = new Response(
    body: $factory->createStreamFromFile('/srv/app/downloads/archive.zip', 'rb'),
    headers: [
        'Content-Type' => 'application/zip',
        'Content-Disposition' => 'attachment; filename="archive.zip"',
    ],
);

$emitter = new SapiStreamEmitter();
$emitter->setMaxBufferSize(64 * 1024);
$emitter->emit($response);
```

The stream emitter honors a valid `Content-Range` response header:

```php
<?php

$partial = $response
    ->withStatus(206)
    ->withHeader('Accept-Ranges', 'bytes')
    ->withHeader('Content-Range', 'bytes 1024-2047/8192')
    ->withHeader('Content-Length', '1024');

$emitter->emit($partial);
```

This emits the selected response-body range; your application is responsible
for parsing the incoming `Range` request header, validating it against the
resource, and constructing the 206 or 416 response.

## Content length

For a stream with a known size, inject `Content-Length` without replacing an
existing value:

```php
<?php

use Qubus\Http\Emitter\HttpUtil;

$response = HttpUtil::injectContentLength($response);
```

Do not inject a length when later middleware will compress, transform, or
otherwise change the response body.

## Emitter middleware

`EmitterMiddleware` emits the downstream response and then returns it:

```php
<?php

use Qubus\Http\Emitter\Middleware\EmitterMiddleware;
use Qubus\Http\Emitter\SapiStreamEmitter;

$emitterMiddleware = new EmitterMiddleware(new SapiStreamEmitter());
```

Place it at the outer edge of a pipeline so it runs after downstream middleware
has completed. A simpler application can omit it and emit the final response in
its front controller.

## HttpPublisher

`HttpPublisher` is a compatibility publisher for response or stream content:

```php
<?php

use Qubus\Http\HttpPublisher;

$publisher = new HttpPublisher();
$publisher->publish($response);
```

It can also delegate a response to a Laminas
`Laminas\HttpHandlerRunner\Emitter\EmitterInterface` implementation:

```php
<?php

$publisher->publish($response, $laminasEmitter);
```

Prefer `SapiEmitter` or `SapiStreamEmitter` in new integrations when you do not
need the Laminas emitter compatibility path.
