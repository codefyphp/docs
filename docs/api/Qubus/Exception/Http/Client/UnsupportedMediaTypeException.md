# UnsupportedMediaTypeException

***

* Full name: `\Qubus\Exception\Http\Client\UnsupportedMediaTypeException`
* Parent class: [`\Qubus\Exception\Exception`](../../Exception.md)

## Methods

### __construct

```php
public __construct(string $message = 'The server is refusing to service the request because the entity ' . 'of the request is in a format not supported by the requested resource for the requested method.', int $code = 415, ?\Throwable $previous = null): mixed
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
