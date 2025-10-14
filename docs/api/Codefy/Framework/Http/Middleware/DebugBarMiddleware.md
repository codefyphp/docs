***

# DebugBarMiddleware





* Full name: `\Codefy\Framework\Http\Middleware\DebugBarMiddleware`
* This class implements:
[`\Psr\Http\Server\MiddlewareInterface`](../../../../Psr/Http/Server/MiddlewareInterface.md)


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`FORCE_KEY`|public| |&#039;X-Enable-Debug-Bar&#039;|

## Properties


### debugBarRenderer



```php
private \DebugBar\JavascriptRenderer $debugBarRenderer
```






***

### responseFactory



```php
private \Psr\Http\Message\ResponseFactoryInterface $responseFactory
```






***

### streamFactory



```php
private \Psr\Http\Message\StreamFactoryInterface|null $streamFactory
```






***

## Methods


### __construct



```php
public __construct(\DebugBar\JavascriptRenderer $debugBarRenderer, \Psr\Http\Message\ResponseFactoryInterface $responseFactory, ?\Psr\Http\Message\StreamFactoryInterface $streamFactory = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$debugBarRenderer` | **\DebugBar\JavascriptRenderer** |  |
| `$responseFactory` | **\Psr\Http\Message\ResponseFactoryInterface** |  |
| `$streamFactory` | **?\Psr\Http\Message\StreamFactoryInterface** |  |





***

### process



```php
public process(\Psr\Http\Message\ServerRequestInterface $request, \Psr\Http\Server\RequestHandlerInterface $handler): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |
| `$handler` | **\Psr\Http\Server\RequestHandlerInterface** |  |





***

### shouldReturnResponse



```php
private shouldReturnResponse(\Psr\Http\Message\ServerRequestInterface $request, \Psr\Http\Message\ResponseInterface $response): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |





***

### prepareHtmlResponseWithDebugBar



```php
private prepareHtmlResponseWithDebugBar(\Psr\Http\Message\ResponseInterface $response): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |





***

### attachDebugBarToHtmlResponse



```php
private attachDebugBarToHtmlResponse(\Psr\Http\Message\ResponseInterface $response): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |





***

### getStaticFile



```php
private getStaticFile(\Psr\Http\Message\UriInterface $uri): ?\Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **\Psr\Http\Message\UriInterface** |  |





***

### extractPath



```php
private extractPath(\Psr\Http\Message\UriInterface $uri): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **\Psr\Http\Message\UriInterface** |  |





***

### getContentTypeByFileName



```php
private getContentTypeByFileName(string $filename): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$filename` | **string** |  |





***

### isHtmlResponse



```php
private isHtmlResponse(\Psr\Http\Message\ResponseInterface $response): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |





***

### isHtmlAccepted



```php
private isHtmlAccepted(\Psr\Http\Message\ServerRequestInterface $request): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |





***

### isHtml



```php
private isHtml(\Psr\Http\Message\MessageInterface $message, string $headerName): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **\Psr\Http\Message\MessageInterface** |  |
| `$headerName` | **string** |  |





***

### isRedirect



```php
private isRedirect(\Psr\Http\Message\ResponseInterface $response): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |





***

### serializeResponse



```php
private serializeResponse(\Psr\Http\Message\ResponseInterface $response): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |





***

### serializeHeaders



```php
private serializeHeaders(array&lt;string,string[]&gt; $headers): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$headers` | **array<string,string[]>** |  |





***

### filterHeader



```php
private filterHeader(string $header): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$header` | **string** |  |





***


***
> Automatically generated on 2025-10-13
