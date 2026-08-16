# Exception

***

* Full name: `\Qubus\Exception\Exception`
* Parent class: [`Exception`](../../Exception.md)

## Properties

### message

Exception message.

```php
protected string $message
```

***

### file

Source filename of exception.

```php
protected string $file
```

***

### line

Source line of exception.

```php
protected int $line
```

***

## Methods

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

- [`Exception`]()

***

### __toString

```php
public __toString(): string
```

***
