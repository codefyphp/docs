# BadGatewayException

***

* Full name: `\Qubus\Exception\Http\Server\BadGatewayException`
* Parent class: [`\Qubus\Exception\Exception`](../../Exception.md)

## Methods

### __construct

```php
public __construct(string $message = 'The server cannot complete the request because a ' . 'downstream process failed to respond properly.', int $code = 502, ?\Throwable $previous = null): mixed
```

**Parameters:**

| Parameter   | Type            | Description |
|-------------|-----------------|-------------|
| `$message`  | **string**      |             |
| `$code`     | **int**         |             |
| `$previous` | **?\Throwable** |             |

***

## Inherited methods

### __construct

```php
public __construct(?string $message = '', int $code = 0, ?\Throwable $previous = null): mixed
```

**Parameters:**

| Parameter   | Type            | Description |
|-------------|-----------------|-------------|
| `$message`  | **?string**     |             |
| `$code`     | **int**         |             |
| `$previous` | **?\Throwable** |             |

**Throws:**

- [`Exception`](../../Exception.md)

***

### __toString

```php
public __toString(): string
```

***
