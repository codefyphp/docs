***

# SapiStreamEmitter





* Full name: `\Qubus\Http\Emitter\SapiStreamEmitter`
* Parent class: [`\Qubus\Http\Emitter\BaseEmitter`](./BaseEmitter.md)
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`CONTENT_PATTERN_REGEX`|private| |&#039;/(?P&lt;unit&gt;[\w]+)\s+(?P&lt;start&gt;\d+)-(?P&lt;end&gt;\d+)\/(?P&lt;size&gt;\d+|\*)/&#039;|

## Properties


### maxBufferSize

Maximum output buffering size for each iteration.

```php
protected int $maxBufferSize
```






***

## Methods


### getMaxBufferSize

Get the value of max buffer size

```php
public getMaxBufferSize(): int
```












***

### setMaxBufferSize

Set the value of max buffer size

```php
public setMaxBufferSize(int $maxBufferSize): \Qubus\Http\Emitter\SapiStreamEmitter
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$maxBufferSize` | **int** |  |




**Throws:**

- [`EmitterException`](./Exceptions/EmitterException.md)



***

### emit

Emit a response.

```php
public emit(\Psr\Http\Message\ResponseInterface $response): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |





***

### emitStream

Emit response body as a stream

```php
private emitStream(\Psr\Http\Message\ResponseInterface $response): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |





***

### emitBody

Emit the response body by max buffer size

```php
private emitBody(\Psr\Http\Message\ResponseInterface $response): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |





***

### emitBodyRange

Emit the range of the response body by max buffer size.

```php
private emitBodyRange(\Psr\Http\Message\ResponseInterface $response, \Qubus\Http\Emitter\ContentRange $range): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |
| `$range` | **\Qubus\Http\Emitter\ContentRange** |  |





***

### getContentRange

Get ContentRange

```php
private getContentRange(\Psr\Http\Message\ResponseInterface $response): \Qubus\Http\Emitter\ContentRange|null
```

Parses the Content-Range header line from the response and generates
ContentRange instance.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |





**See Also:**

* http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.16 - 

***


## Inherited methods


### assertNoPreviousOutput

Assert either that no headers have been sent
or the output buffer contains no content.

```php
protected assertNoPreviousOutput(): void
```












***

### emitStatusLine

Emit the status line.

```php
protected emitStatusLine(\Psr\Http\Message\ResponseInterface $response): void
```

Emits the status line using the protocol version and status code from
the response; if a reason phrase is available, it, too, is emitted.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |





***

### emitHeaders

Emit response headers.

```php
protected emitHeaders(\Psr\Http\Message\ResponseInterface $response): void
```

Loops through each header, emitting each; if the header value
is an array with multiple values, ensures that each is sent
in such a way as to create aggregate headers (instead of replace
the previous).






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |





***

### normalizeHeaderName

Normalize a header name

```php
private normalizeHeaderName(string $headerName): string
```

Normalized header will be in the following format: Example-Header-Name






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$headerName` | **string** |  |





***

### header



```php
private header(string $headerName, bool $replace, int $statusCode): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$headerName` | **string** |  |
| `$replace` | **bool** |  |
| `$statusCode` | **int** |  |





***

### closeConnection



```php
protected closeConnection(): void
```












***

### emit

Emit a response.

```php
public emit(\Psr\Http\Message\ResponseInterface $response): void
```




* This method is **abstract**.



**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |





***


***
> Automatically generated on 2025-10-13
