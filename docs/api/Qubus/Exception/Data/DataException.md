# DataException

***

* Full name: `\Qubus\Exception\Data\DataException`
* Parent class: [`\Qubus\Exception\Exception`](../Exception.md)

## Methods

### __construct

```php
public __construct(string $message = 'The requested data cannot be found in the data source.', int $code = 404, ?\Throwable $previous = null): mixed
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
