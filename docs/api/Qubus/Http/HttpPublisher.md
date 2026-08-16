# HttpPublisher

StreamPublisher publishes the given response.

***

* Full name: `\Qubus\Http\HttpPublisher`
* This class implements:
  [`\Qubus\Http\Publisher`](./Publisher.md)

## Methods

### publish

Publish the content.

```php
public publish(\Psr\Http\Message\ResponseInterface|\Psr\Http\Message\StreamInterface $content, ?\Laminas\HttpHandlerRunner\Emitter\EmitterInterface $response): bool|\Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter   | Type                                                                       | Description |
|-------------|----------------------------------------------------------------------------|-------------|
| `$content`  | **\Psr\Http\Message\ResponseInterface\|\Psr\Http\Message\StreamInterface** |             |
| `$response` | **?\Laminas\HttpHandlerRunner\Emitter\EmitterInterface**                   |             |

**Throws:**

- [`\LogicException|\Exception`](../../LogicException|/Exception.md)

***

### emitStreamBody

Emit the message body.

```php
private emitStreamBody(\Psr\Http\Message\StreamInterface $body): bool
```

**Parameters:**

| Parameter | Type                                  | Description |
|-----------|---------------------------------------|-------------|
| `$body`   | **\Psr\Http\Message\StreamInterface** |             |

***

### emitResponseHeaders

Emit the response header.

```php
private emitResponseHeaders(\Psr\Http\Message\ResponseInterface $response): void
```

**Parameters:**

| Parameter   | Type                                    | Description |
|-------------|-----------------------------------------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |             |

***
