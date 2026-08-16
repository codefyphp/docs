# SapiEmitter

***

* Full name: `\Qubus\Http\Emitter\SapiEmitter`
* Parent class: [`\Qubus\Http\Emitter\BaseEmitter`](./BaseEmitter.md)

## Methods

### emit

Emit a response.

```php
public emit(\Psr\Http\Message\ResponseInterface $response): void
```

**Parameters:**

| Parameter   | Type                                    | Description |
|-------------|-----------------------------------------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |             |

***

### emitBody

Emit the response body

```php
private emitBody(\Psr\Http\Message\ResponseInterface $response): void
```

**Parameters:**

| Parameter   | Type                                    | Description |
|-------------|-----------------------------------------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |             |

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

| Parameter   | Type                                    | Description |
|-------------|-----------------------------------------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |             |

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

| Parameter   | Type                                    | Description |
|-------------|-----------------------------------------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |             |

***

### normalizeHeaderName

Normalize a header name

```php
private normalizeHeaderName(string $headerName): string
```

Normalized header will be in the following format: Example-Header-Name

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$headerName` | **string** |             |

***

### header

```php
private header(string $headerName, bool $replace, int $statusCode): void
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$headerName` | **string** |             |
| `$replace`    | **bool**   |             |
| `$statusCode` | **int**    |             |

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

| Parameter   | Type                                    | Description |
|-------------|-----------------------------------------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |             |

***
