# RequestEntityTooLargeException

***

* Full name: `\Qubus\Exception\Http\Client\RequestEntityTooLargeException`
* Parent class: [`\Qubus\Exception\Exception`](../../Exception.md)

## Methods

### __construct

```php
public __construct(string $message = 'The server is refusing to process a request because the message is ' . 'larger than the server is willing or able to process.', int $code = 413, ?\Throwable $previous = null): mixed
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
