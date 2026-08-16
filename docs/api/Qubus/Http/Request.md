# Request

***

* Full name: `\Qubus\Http\Request`
* Parent class: [`Request`](../../Laminas/Diactoros/Request.md)
* This class is marked as **final** and can't be subclassed
* This class implements:
  `RequestInterface`
* This class is a **Final class**

## Constants

| Constant                      | Visibility | Type | Value                               |
|-------------------------------|------------|------|-------------------------------------|
| `REQUEST_TYPE_GET`            | public     |      | 'get'                               |
| `REQUEST_TYPE_POST`           | public     |      | 'post'                              |
| `REQUEST_TYPE_PUT`            | public     |      | 'put'                               |
| `REQUEST_TYPE_PATCH`          | public     |      | 'patch'                             |
| `REQUEST_TYPE_OPTIONS`        | public     |      | 'options'                           |
| `REQUEST_TYPE_DELETE`         | public     |      | 'delete'                            |
| `REQUEST_TYPE_HEAD`           | public     |      | 'head'                              |
| `CONTENT_TYPE_JSON`           | public     |      | 'application/json'                  |
| `CONTENT_TYPE_FORM_DATA`      | public     |      | 'multipart/form-data'               |
| `CONTENT_TYPE_X_FORM_ENCODED` | public     |      | 'application/x-www-form-urlencoded' |
| `FORCE_METHOD_KEY`            | public     |      | '_method'                           |

## Properties

### requestTypes

All request-types

```php
public static string[] $requestTypes
```

* This property is **static**.

***

### requestTypesPost

Post request-types.

```php
public static string[] $requestTypesPost
```

* This property is **static**.

***

### data

Additional data.

```php
private array $data
```

***

### httpHeaders

Server headers.

```php
protected array $httpHeaders
```

***

### contentType

Request ContentType

```php
protected string $contentType
```

***

### host

Request host.

```php
protected ?string $host
```

***

### url

Current request url.

```php
protected ?\Qubus\Http\Url $url
```

***

### method

Request method.

```php
protected ?string $method
```

***

### inputHandler

Input handler.

```php
protected ?\Qubus\Http\Input\Handler $inputHandler
```

***

### hasPendingRewrite

Defines if request has pending rewrite.

```php
protected bool $hasPendingRewrite
```

***

### rewriteUrl

Rewrite url.

```php
protected ?string $rewriteUrl
```

***

## Methods

### __construct

```php
public __construct(null|string|\Psr\Http\Message\UriInterface $uri = null, null|string $method = null, string|resource|\Psr\Http\Message\StreamInterface $body = 'php://temp', array $headers = []): mixed
```

**Parameters:**

| Parameter  | Type                                                    | Description                          |
|------------|---------------------------------------------------------|--------------------------------------|
| `$uri`     | **null\|string\|\Psr\Http\Message\UriInterface**        | URI for the request, if any.         |
| `$method`  | **null\|string**                                        | HTTP method for the request, if any. |
| `$body`    | **string\|resource\|\Psr\Http\Message\StreamInterface** | Message body, if any.                |
| `$headers` | **array**                                               | Headers for the message, if any.     |

**Throws:**

For any invalid value.
- [`\Qubus\Http\Exception\MalformedUrlException|\InvalidArgumentException`](./Exception/MalformedUrlException|/InvalidArgumentException.md)

***

### isSecure

```php
public isSecure(): bool
```

***

### getUrl

```php
public getUrl(): \Qubus\Http\Url
```

***

### getUrlCopy

Copy url object.

```php
public getUrlCopy(): \Qubus\Http\Url
```

***

### getHost

```php
public getHost(): ?string
```

***

### getAuthUser

Get http basic auth user.

```php
public getAuthUser(): ?string
```

***

### getAuthPassword

Get http basic auth password.

```php
public getAuthPassword(): ?string
```

***

### getHttpHeaders

Get all headers.

```php
public getHttpHeaders(): array
```

***

### getIp

Get ip address.

```php
public getIp(bool $safeMode = false): string|null
```

If $safeMode is false, this function will detect Proxys.
But the user can edit this header to whatever he wants!
https://stackoverflow.com/questions/3003145/how-to-get-the-client-ip-address-in-php#comment-25086804

**Parameters:**

| Parameter   | Type     | Description                                                                                                  |
|-------------|----------|--------------------------------------------------------------------------------------------------------------|
| `$safeMode` | **bool** | When enabled, only safe non-spoofable
headers will be returned. Note this
can cause issues when using proxy. |

***

### getRemoteAddr

Get remote address/ip

```php
public getRemoteAddr(): string|null
```

***

### getReferer

Get referer.

```php
public getReferer(): ?string
```

***

### getUserAgent

Get user agent.

```php
public getUserAgent(): ?string
```

***

### getHttpHeader

Get header value by name

```php
public getHttpHeader(string $name, string|mixed|null $defaultValue = null, bool $tryParse = true): ?string
```

**Parameters:**

| Parameter       | Type                    | Description                                                                                                                       |
|-----------------|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| `$name`         | **string**              | Name of the header.                                                                                                               |
| `$defaultValue` | **string\|mixed\|null** | Value to be returned if header is not found.                                                                                      |
| `$tryParse`     | **bool**                | When enabled the method will try to find the header
from both client (http) and server-side variants,
if the header is not found. |

***

### getFirstHeader

Will try to find first header from list of headers.

```php
public getFirstHeader(array $headers, mixed|null $defaultValue = null): mixed|null
```

**Parameters:**

| Parameter       | Type            | Description |
|-----------------|-----------------|-------------|
| `$headers`      | **array**       |             |
| `$defaultValue` | **mixed\|null** |             |

***

### getContentType

Gets content type which request has been made.

```php
public getContentType(): string|null
```

***

### withContentType

Set request content-type

```php
protected withContentType(string $contentType): $this
```

**Parameters:**

| Parameter      | Type       | Description |
|----------------|------------|-------------|
| `$contentType` | **string** |             |

***

### handler

Get input class

```php
public handler(): \Qubus\Http\Input\Handler
```

***

### isFormatAccepted

Is format accepted

```php
public isFormatAccepted(string $format): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$format` | **string** |             |

***

### isAjax

Returns true if the request is made through Ajax

```php
public isAjax(): bool
```

***

### getBasicAuth

Gets auth info accepted by the browser/client.

```php
public getBasicAuth(): array|null
```

***

### getDigestAuth

Gets auth info accepted by the browser/client.

```php
public getDigestAuth(): array
```

***

### getClientAddress

Gets most possible client IPv4 Address.

```php
public getClientAddress(bool $trustForwardedHeader = false): bool|string
```

**Parameters:**

| Parameter               | Type     | Description |
|-------------------------|----------|-------------|
| `$trustForwardedHeader` | **bool** |             |

***

### getServerAddress

Gets active server address IP.

```php
public getServerAddress(): string
```

***

### getServerName

Gets active server name.

```php
public getServerName(): string
```

***

### getScheme

Gets HTTP schema (http/https).

```php
public getScheme(): string
```

***

### getServer

Gets variable from $_SERVER super global.

```php
public getServer(string $name): ?string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### hasServer

Checks whether $_SERVER super global has certain index.

```php
final public hasServer(string $name): string
```

* This method is **final**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### isPostBack

Returns true when request-method is type that could contain data in the page body.

```php
public isPostBack(): bool
```

***

### getAcceptFormats

Get accept formats.

```php
public getAcceptFormats(): array
```

***

### setUrl

```php
public setUrl(\Qubus\Http\Url $url): void
```

**Parameters:**

| Parameter | Type                | Description |
|-----------|---------------------|-------------|
| `$url`    | **\Qubus\Http\Url** |             |

***

### setHost

```php
public setHost(?string $host): void
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$host`   | **?string** |             |

***

### setMethod

```php
public setMethod(string $method): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$method` | **string** |             |

***

### getRewriteUrl

Get rewrite url.

```php
public getRewriteUrl(): ?string
```

***

### setRewriteUrl

Set rewrite url.

```php
public setRewriteUrl(string $rewriteUrl): $this
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$rewriteUrl` | **string** |             |

***

### isMethod

Does this request use a given method?

```php
public isMethod(string $method): bool
```

**Parameters:**

| Parameter | Type       | Description  |
|-----------|------------|--------------|
| `$method` | **string** | HTTP method. |

***

### isDelete

Checks whether HTTP method is DELETE.

```php
public isDelete(): bool
```

***

### isGet

Checks whether HTTP method is GET.

```php
public isGet(): bool
```

***

### isHead

Checks whether HTTP method is HEAD.

```php
public isHead(): bool
```

***

### isOptions

Checks whether HTTP method is OPTIONS.

```php
public isOptions(): bool
```

***

### isPatch

Checks whether HTTP method is PATCH.

```php
public isPatch(): bool
```

***

### isPost

Checks whether HTTP method is POST.

```php
public isPost(): bool
```

***

### isPut

Checks whether HTTP method is PUT.

```php
public isPut(): bool
```

***

### isConnect

Checks whether HTTP method is CONNECT.

```php
public isConnect(): bool
```

***

### isTrace

Checks whether HTTP method is TRACE.

```php
public isTrace(): bool
```

***

### isValidHttpMethod

Checks if a method is a valid HTTP method.

```php
public isValidHttpMethod(string $method): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$method` | **string** |             |

***

### getServerArray

```php
protected getServerArray(): array
```

***

### __isset

```php
public __isset(string $name): mixed
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### __set

```php
public __set(string $name, ?string $value = null): mixed
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$name`   | **string**  |             |
| `$value`  | **?string** |             |

***

### __get

```php
public __get(string $name): mixed
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***
