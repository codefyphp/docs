***

# ServerRequest





* Full name: `\Qubus\Http\Swoole\ServerRequest`
* Parent class: [`\Qubus\Http\Swoole\Request`](./Request.md)
* This class implements:
[`\Psr\Http\Message\ServerRequestInterface`](../../../Psr/Http/Message/ServerRequestInterface.md)



## Properties


### attributes



```php
private array $attributes
```






***

### cookies



```php
private array $cookies
```






***

### files



```php
private array $files
```






***

### parsedBody



```php
private null|array|object $parsedBody
```






***

### parsedBodyIsSet



```php
private bool $parsedBodyIsSet
```






***

### query



```php
private array $query
```






***

### uploadedFileFactory



```php
private \Psr\Http\Message\UploadedFileFactoryInterface $uploadedFileFactory
```






***

## Methods


### __construct



```php
public __construct(\Swoole\Http\Request $swooleRequest, \Psr\Http\Message\UriFactoryInterface $uriFactory, \Psr\Http\Message\StreamFactoryInterface $streamFactory, \Psr\Http\Message\UploadedFileFactoryInterface $uploadedFileFactory): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$swooleRequest` | **\Swoole\Http\Request** |  |
| `$uriFactory` | **\Psr\Http\Message\UriFactoryInterface** |  |
| `$streamFactory` | **\Psr\Http\Message\StreamFactoryInterface** |  |
| `$uploadedFileFactory` | **\Psr\Http\Message\UploadedFileFactoryInterface** |  |





***

### getServerParams



```php
public getServerParams(): array
```












***

### getCookieParams



```php
public getCookieParams(): array
```












***

### withCookieParams



```php
public withCookieParams(array $cookies): \Psr\Http\Message\ServerRequestInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$cookies` | **array** |  |





***

### getQueryParams



```php
public getQueryParams(): array
```












***

### withQueryParams



```php
public withQueryParams(array $query): \Psr\Http\Message\ServerRequestInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$query` | **array** |  |





***

### getUploadedFiles



```php
public getUploadedFiles(): array
```












***

### withUploadedFiles



```php
public withUploadedFiles(array $uploadedFiles): \Psr\Http\Message\ServerRequestInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uploadedFiles` | **array** |  |





***

### getParsedBody



```php
public getParsedBody(): object|array|null
```












***

### withParsedBody



```php
public withParsedBody(mixed $data): \Psr\Http\Message\ServerRequestInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **mixed** |  |





***

### getAttributes



```php
public getAttributes(): array
```












***

### getAttribute



```php
public getAttribute(string $name, mixed $default = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$default` | **mixed** |  |





***

### withAttribute



```php
public withAttribute(string $name, mixed $value): \Psr\Http\Message\ServerRequestInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$value` | **mixed** |  |





***

### withoutAttribute



```php
public withoutAttribute(string $name): \Psr\Http\Message\ServerRequestInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***


## Inherited methods


### __construct



```php
public __construct(\Swoole\Http\Request $swooleRequest, \Psr\Http\Message\UriFactoryInterface $uriFactory, \Psr\Http\Message\StreamFactoryInterface $streamFactory): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$swooleRequest` | **\Swoole\Http\Request** |  |
| `$uriFactory` | **\Psr\Http\Message\UriFactoryInterface** |  |
| `$streamFactory` | **\Psr\Http\Message\StreamFactoryInterface** |  |





***

### getRequestTarget



```php
public getRequestTarget(): string
```












***

### withRequestTarget



```php
public withRequestTarget(string $requestTarget): \Psr\Http\Message\RequestInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$requestTarget` | **string** |  |





***

### getMethod



```php
public getMethod(): string
```












***

### withMethod



```php
public withMethod(string $method): \Psr\Http\Message\RequestInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$method` | **string** |  |





***

### getUri



```php
public getUri(): \Psr\Http\Message\UriInterface
```












***

### withUri



```php
public withUri(\Psr\Http\Message\UriInterface $uri, bool $preserveHost = false): \Psr\Http\Message\RequestInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **\Psr\Http\Message\UriInterface** |  |
| `$preserveHost` | **bool** |  |





***

### getProtocolVersion



```php
public getProtocolVersion(): string
```












***

### withProtocolVersion



```php
public withProtocolVersion(string $version): \Psr\Http\Message\MessageInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$version` | **string** |  |





***

### getHeaders



```php
public getHeaders(): array
```












***

### hasHeader



```php
public hasHeader(mixed $name): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |





***

### getHeader



```php
public getHeader(string $name): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### getHeaderLine



```php
public getHeaderLine(string $name): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### withHeader



```php
public withHeader(string $name, mixed $value): \Psr\Http\Message\MessageInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$value` | **mixed** |  |





***

### withAddedHeader



```php
public withAddedHeader(string $name, mixed $value): \Psr\Http\Message\MessageInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$value` | **mixed** |  |





***

### withoutHeader



```php
public withoutHeader(string $name): \Psr\Http\Message\MessageInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### getBody



```php
public getBody(): \Psr\Http\Message\StreamInterface
```












***

### withBody



```php
public withBody(\Psr\Http\Message\StreamInterface $body): \Psr\Http\Message\MessageInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$body` | **\Psr\Http\Message\StreamInterface** |  |





***


***
> Automatically generated on 2025-10-13
