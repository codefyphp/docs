# NotFoundException

***

* Full name: `\Qubus\Exception\Http\Client\NotFoundException`
* Parent class: [`\Qubus\Exception\Exception`](../../Exception.md)

## Methods

### __construct

```php
public __construct(string $message = 'The requested entity cannot be found, this may be returned because ' . 'the entity is not accessible using requested credentials because of a recent state ' . 'change or because the entity cannot be found at all.', int $code = 404, ?\Throwable $previous = null): mixed
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
