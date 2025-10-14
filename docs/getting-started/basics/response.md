---
title: Response
sidebar_title: Response
weight: 8
---

`Qubus\Http\Request`, `Qubus\Http\Response`, and `Qubus\Http\ServerRequest` are all wrappers for [laminas-diactoros](https://docs.laminas.dev/laminas-diactoros/v3/api/). 
Check out diactoros's documentation on its api and usage. Those classes provide an object-oriented way to interact with 
HTTP requests and responses.

## Response

A response is an HTTP message a client receives from a server after sending an HTTP request message. Like `Request` 
and `ServerRequest`, responses are immutable. `Qubus\Http\Response` is a wrapper around a 
[Psr\Http\Message\ResponseInterface](https://github.com/php-fig/http-message/blob/master/src/ResponseInterface.php) 
implementation. Any methods that would change state — those prefixed with `with` and 
`without` — all return a new instance with the changes requested.

    <?php
    
    use Qubus\Http\Response;
    
    $response = new Response(body: 'Content', status: '200', headers: ['content-type' => 'text/html']);

### HtmlResponse and JsonResponse

The most common use case in server-side applications for generating responses is to provide a string to use for the 
response, typically HTML or data to serialize as JSON. `Qubus\Http\Factories\HtmlResponseFactory` and
`Qubus\Http\Factories\JsonResponseFactory` exist to facilitate these use cases:

    <?php
    
    $htmlResponse = HtmlResponseFactory::create($html);
    
    $jsonResponse = JsonResponseFactory::create($data);

In the first example, you will receive a response with a stream containing the HTML; additionally, the `Content-Type` 
header will be set to `text/html`. In the second case, the stream will contain a stream containing the JSON-serialized 
`$data`, and have a `Content-Type` header set to `application/json`.

Both objects allow passing the HTTP status, and any headers you want to specify, including the `Content-Type` header:

    <?php

    $htmlResponse = HtmlResponseFactory::create($html, 404, [
        'Content-Type' => [ 'application/xhtml+xml' ],
    ]);
    
    $jsonResponse = JsonResponseFactory::create($data, 422, [
        'Content-Type' => [ 'application/problem+json' ],
    ]);

