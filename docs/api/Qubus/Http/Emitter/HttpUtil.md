# HttpUtil

***

* Full name: `\Qubus\Http\Emitter\HttpUtil`

## Methods

### __construct

Private constructor; non-instantiable.

```php
private __construct(): mixed
```

***

### injectContentLength

Inject the Content-Length header if is not already present.

```php
public static injectContentLength(\Psr\Http\Message\ResponseInterface $response): \Psr\Http\Message\ResponseInterface
```

* This method is **static**.
**Parameters:**

| Parameter   | Type                                    | Description |
|-------------|-----------------------------------------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |             |

***

### closeOutputBuffers

Cleans or flushes output buffers up to target level.

```php
public static closeOutputBuffers(int $maxBufferLevel, bool $flush): void
```

Resulting level can be greater than target level if
a non-removable buffer has been encountered.

* This method is **static**.
**Parameters:**

| Parameter         | Type     | Description                           |
|-------------------|----------|---------------------------------------|
| `$maxBufferLevel` | **int**  | The target output buffering level     |
| `$flush`          | **bool** | Whether to flush or clean the buffers |

***
