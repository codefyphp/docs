***

# Request





* Full name: `\Qubus\Http\Swoole\Request`
* This class implements:
[`\Psr\Http\Message\RequestInterface`](../../../Psr/Http/Message/RequestInterface.md)



## Properties


### body



```php
private \Psr\Http\Message\StreamInterface $body
```






***

### headers



```php
private ?array $headers
```






***

### method



```php
private string $method
```






***

### protocol



```php
private string $protocol
```






***

### requestTarget



```php
private string $requestTarget
```






***

### uri



```php
private \Psr\Http\Message\UriInterface $uri
```






***

### swooleRequest



```php
public \Swoole\Http\Request $swooleRequest
```






***

### uriFactory



```php
protected \Psr\Http\Message\UriFactoryInterface $uriFactory
```






***

### streamFactory



```php
protected \Psr\Http\Message\StreamFactoryInterface $streamFactory
```






***

## Methods


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

### buildRequestTarget



```php
private buildRequestTarget(): string
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

### parseUserInfo



```php
private parseUserInfo(): false|string|null
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

### shouldUpdateHostHeader



```php
private shouldUpdateHostHeader(mixed $preserveHost): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$preserveHost` | **mixed** |  |





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

### initHeadersList



```php
private initHeadersList(): void
```












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
