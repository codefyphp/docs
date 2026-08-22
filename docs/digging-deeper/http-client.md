---
title: HTTP Client
sidebar_title: HTTP Client
summary: Send HTTP requests from CodefyPHP with a configurable PHP client, PSR interfaces, request options, responses, and error handling.
keywords: php-http-client,psr-http,codefyphp
order: 24
---

## Installation

```shell
composer require qubus/http
```

## Introduction

`Codefy\Framework\Http\HttpClient` makes it easy to send HTTP requests:

    <?php
    
    use Codefy\Framework\Http\HttpClient;
    
    $res = HttpClient::factory()->request('GET', 'https://codefy.ddev.site:33001/');
    
    echo $res->getStatusCode() . "\n";
    // "200"
    echo $res->getHeader('content-type')[0] . "\n";
    // 'text/html; charset=utf-8'

!!! info "Guzzle Http Client Wrapper"
    `HttpClient` is a lightweight wrapper around Guzzle’s client. This guide is a condensed adaptation of Guzzle’s own 
    documentation, focusing on the `factory()` method and core API. Use it as a quick start to get familiar with 
    `HttpClient`, and refer to Guzzle’s excellent [documentation](https://docs.guzzlephp.org/en/stable/index.html) for 
    a deeper dive into all available features and API.

## Making a Request

You can send requests using a `GuzzleHttp\ClientInterface` object.

### Creating A Client

    <?php
    
    use Codefy\Framework\Http\HttpClient;
    
    $client = HttpClient::factory([
        // Base URI is used with relative requests
        'base_uri' => 'http://httpbin.org',
        // You can set any number of default request options.
        'timeout'  => 2.0,
    ]);

Clients are immutable in Guzzle, which means that you cannot change the defaults used by a client after it's created.

The client's `factory()` method accepts an associative array of options (`base_uri`, `timeout`, and many more):

#### base_uri

(string|UriInterface) Base URI of the client that is merged into relative URIs. Can be a string or 
instance of `Psr\Http\Message\UriInterface`. When a relative URI is provided to a client, the client will combine the 
base URI with the relative URI.

    <?php
    
    use Codefy\Framework\Http\HttpClient;
    
    // Create a client with a base URI
    $client = HttpClient::factory(['base_uri' => 'http://httpbin.org']);
    // Send a request to https://foo.com/api/test
    $response = $client->request('GET', 'test');
    // Send a request to https://foo.com/root
    $response = $client->request('GET', '/root');


#### timeout

Float describing the total timeout of the request in seconds. Use `0` to wait indefinitely 
(the default behavior).

    <?php
    
    // Timeout if a server does not return a response in 3.14 seconds.
    $client->request('GET', '/delay/5', ['timeout' => 3.14]);
    // PHP Fatal error:  Uncaught exception 'GuzzleHttp\Exception\TransferException'
