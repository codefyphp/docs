# HttpClient

***

* Full name: `\Codefy\Framework\Http\HttpClient`
* Parent class: [`Client`](../../../GuzzleHttp/Client.md)

## Methods

### __construct

```php
public __construct((array|int|string|callable|bool|\Psr\Http\Message\UriInterface)[] $config = []): mixed
```

**Parameters:**

| Parameter | Type                                                                       | Description |
|-----------|----------------------------------------------------------------------------|-------------|
| `$config` | **(array\|int\|string\|callable\|bool\|\Psr\Http\Message\UriInterface)[]** |             |

***

### factory

```php
public static factory(): self
```

* This method is **static**.
***

### request

{@inheritDoc}

```php
public request(string $method, string|\Psr\Http\Message\UriInterface $uri = '', array $options = []): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter  | Type                                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|------------|--------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `$method`  | **string**                                 | HTTP method.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `$uri`     | **string\|\Psr\Http\Message\UriInterface** | URL, URI object or string.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `$options` | **array**                                  | {
                                   Optional. Array of Request options to apply.
                                   See \GuzzleHttp\RequestOptions.

    @type string                            $method             Request method. Accepts 'GET', 'POST', 'HEAD',
                                                                'PUT', 'DELETE', 'TRACE', 'OPTIONS', or 'PATCH'.
                                                                Default: 'GET'.
    @type float                             $timeout            Float describing the total timeout of the
                                                                request in seconds. Use 0 to wait indefinitely.
                                                                Default 10.
    @type float                             $connect_timeout    Float describing the number of seconds to wait
                                                                while trying to connect to a server. Use 0 to
                                                                wait indefinitely. Default 10.
    @type bool\|array                        $allow_redirects    Describes the redirect behavior of a request.
                                                                Default: false.
    @type float\|int                         $delay              The number of milliseconds to delay before
                                                                sending the request. Default: null.
    @type string                            $version            HTTP protocol version (usually '1.1', '1.0' or
                                                                '2'). Default: '1.1'.
    @type bool                              $http_errors        Set to false to disable throwing exceptions on
                                                                an HTTP protocol errors
                                                                (i.e., 4xx and 5xx responses). Default: true.
    @type string\|array                      $proxy              Whether to enable keep-alive connections with
                                                                the server. Useful and might improve performance
                                                                if several consecutive requests to the same
                                                                server are performed. Default: false.
    @type array                             $headers            Array of headers to send with the request.
                                                                Default: [].
    @type string\|resource\|StreamInterface   $body               Used to control the body of an entity enclosing
                                                                request (e.g., PUT, POST, PATCH). Default: ''.
    @type bool                              $stream             Set to true to stream a response rather than
                                                                download it all up-front. Default: false.
} |

**Throws:**

- [`InvalidArgumentException`](../../../Psr/SimpleCache/InvalidArgumentException.md)
- [`Exception`](../../../Qubus/Exception/Exception.md)
- [`\Exception|\GuzzleHttp\Exception\GuzzleException`](../../../Exception|/GuzzleHttp/Exception/GuzzleException.md)

***
