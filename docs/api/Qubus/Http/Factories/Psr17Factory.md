***

# Psr17Factory





* Full name: `\Qubus\Http\Factories\Psr17Factory`
* Parent class: [`\Qubus\Http\Factories\RequestFactory`](./RequestFactory.md)
* This class implements:
[`\Psr\Http\Message\UriFactoryInterface`](../../../Psr/Http/Message/UriFactoryInterface.md), [`\Psr\Http\Message\UploadedFileFactoryInterface`](../../../Psr/Http/Message/UploadedFileFactoryInterface.md), [`\Psr\Http\Message\StreamFactoryInterface`](../../../Psr/Http/Message/StreamFactoryInterface.md), [`\Psr\Http\Message\ServerRequestFactoryInterface`](../../../Psr/Http/Message/ServerRequestFactoryInterface.md), [`\Psr\Http\Message\ResponseFactoryInterface`](../../../Psr/Http/Message/ResponseFactoryInterface.md)




## Methods


### createResponse



```php
public createResponse(int $code = 200, string $reasonPhrase = &#039;&#039;): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$code` | **int** |  |
| `$reasonPhrase` | **string** |  |





***

### createServerRequest



```php
public createServerRequest(string $method, mixed $uri, array $serverParams = []): \Psr\Http\Message\ServerRequestInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$method` | **string** |  |
| `$uri` | **mixed** |  |
| `$serverParams` | **array** |  |





***

### createStream



```php
public createStream(string $content = &#039;&#039;): \Psr\Http\Message\StreamInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$content` | **string** |  |





***

### createStreamFromFile



```php
public createStreamFromFile(string $filename, string $mode = &#039;r&#039;): \Psr\Http\Message\StreamInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$filename` | **string** |  |
| `$mode` | **string** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### createStreamFromResource



```php
public createStreamFromResource(mixed $resource): \Psr\Http\Message\StreamInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$resource` | **mixed** |  |





***

### createUploadedFile



```php
public createUploadedFile(\Psr\Http\Message\StreamInterface $stream, ?int $size = null, int $error = UPLOAD_ERR_OK, ?string $clientFilename = null, ?string $clientMediaType = null): \Psr\Http\Message\UploadedFileInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$stream` | **\Psr\Http\Message\StreamInterface** |  |
| `$size` | **?int** |  |
| `$error` | **int** |  |
| `$clientFilename` | **?string** |  |
| `$clientMediaType` | **?string** |  |





***

### createUri



```php
public createUri(string $uri = &#039;&#039;): \Psr\Http\Message\UriInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |




**Throws:**

- [`MalformedUrlException`](../Exception/MalformedUrlException.md)



***


## Inherited methods


### createRequest



```php
public createRequest(string $method, mixed $uri): \Psr\Http\Message\RequestInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$method` | **string** |  |
| `$uri` | **mixed** |  |




**Throws:**

- [`MalformedUrlException`](../Exception/MalformedUrlException.md)



***


***
> Automatically generated on 2025-10-13
