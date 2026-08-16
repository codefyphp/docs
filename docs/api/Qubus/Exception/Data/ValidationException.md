# ValidationException

***

* Full name: `\Qubus\Exception\Data\ValidationException`
* Parent class: [`\Qubus\Exception\Exception`](../Exception.md)

## Methods

### __construct

```php
public __construct(?string $message = 'The provided data does not conform to business model or basic domain validation rules.', mixed $code = 0, mixed $previous = null): mixed
```

**Parameters:**

| Parameter   | Type        | Description |
|-------------|-------------|-------------|
| `$message`  | **?string** |             |
| `$code`     | **mixed**   |             |
| `$previous` | **mixed**   |             |

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
