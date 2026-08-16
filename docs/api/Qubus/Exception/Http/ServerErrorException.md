# ServerErrorException

***

* Full name: `\Qubus\Exception\Http\ServerErrorException`
* Parent class: [`\Qubus\Exception\Exception`](../Exception.md)

## Methods

### __construct

```php
public __construct(string $message = 'The server encountered an unexpected condition ' . 'which prevented it from fulfilling the request.', int $code = 500, ?\Throwable $previous = null): mixed
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

- [`Exception`](../Exception.md)

***

### __toString

```php
public __toString(): string
```

***
