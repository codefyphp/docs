***

# HttpClient





* Full name: `\Codefy\Framework\Http\HttpClient`
* Parent class: [`Client`](../../../GuzzleHttp/Client.md)




## Methods


### __construct



```php
public __construct(array $config = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$config` | **array** |  |





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
public request(string $method, string|\Psr\Http\Message\UriInterface $uri = &#039;&#039;, array $options = []): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$method` | **string** | HTTP method. |
| `$uri` | **string&#124;\Psr\Http\Message\UriInterface** | URL, URI object or string. |
| `$options` | **array** | {<br />                                   Optional. Array of Request options to apply.<br />                                   See \GuzzleHttp\RequestOptions.<br /><br />    @type string                            $method             Request method. Accepts &#039;GET&#039;, &#039;POST&#039;, &#039;HEAD&#039;,<br />                                                                &#039;PUT&#039;, &#039;DELETE&#039;, &#039;TRACE&#039;, &#039;OPTIONS&#039;, or &#039;PATCH&#039;.<br />                                                                Default: &#039;GET&#039;.<br />    @type float                             $timeout            Float describing the total timeout of the<br />                                                                request in seconds. Use 0 to wait indefinitely.<br />                                                                Default 10.<br />    @type float                             $connect_timeout    Float describing the number of seconds to wait<br />                                                                while trying to connect to a server. Use 0 to<br />                                                                wait indefinitely. Default 10.<br />    @type bool&amp;#124;array                        $allow_redirects    Describes the redirect behavior of a request.<br />                                                                Default: false.<br />    @type float&amp;#124;int                         $delay              The number of milliseconds to delay before<br />                                                                sending the request. Default: null.<br />    @type string                            $version            HTTP protocol version (usually &#039;1.1&#039;, &#039;1.0&#039; or<br />                                                                &#039;2&#039;). Default: &#039;1.1&#039;.<br />    @type bool                              $http_errors        Set to false to disable throwing exceptions on<br />                                                                an HTTP protocol errors<br />                                                                (i.e., 4xx and 5xx responses). Default: true.<br />    @type string&amp;#124;array                      $proxy              Whether to enable keep-alive connections with<br />                                                                the server. Useful and might improve performance<br />                                                                if several consecutive requests to the same<br />                                                                server are performed. Default: false.<br />    @type array                             $headers            Array of headers to send with the request.<br />                                                                Default: [].<br />    @type string&amp;#124;resource&amp;#124;StreamInterface   $body               Used to control the body of an entity enclosing<br />                                                                request (e.g., PUT, POST, PATCH). Default: &#039;&#039;.<br />    @type bool                              $stream             Set to true to stream a response rather than<br />                                                                download it all up-front. Default: false.<br />} |




**Throws:**

- [`InvalidArgumentException`](../../../Psr/SimpleCache/InvalidArgumentException.md)

- [`Exception`](../../../Qubus/Exception/Exception.md)

- [`\Exception|\GuzzleHttp\Exception\GuzzleException`](../../../Exception|/GuzzleHttp/Exception/GuzzleException.md)



***


***
> Automatically generated on 2025-10-13
