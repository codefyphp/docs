***

# ValidationException

Qubus Exception Class

This extends the default `BaseException` class to allow converting
exceptions to and from `Error` objects.

Unfortunately, because an `Error` object may contain multiple messages and error
codes, only the first message for the first error code in the instance will be
accessible through the exception's methods.

* Full name: `\Qubus\Exception\Data\ValidationException`
* Parent class: [`\Qubus\Exception\Exception`](../Exception.md)




## Methods


### __construct



```php
public __construct(?string $message = &#039;The provided data does not conform to business model or basic domain validation rules.&#039;, mixed $code, mixed $previous = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **?string** |  |
| `$code` | **mixed** |  |
| `$previous` | **mixed** |  |





***


## Inherited methods


### __construct



```php
public __construct(?string $message = &#039;&#039;, int $code, ?\Throwable $previous = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **?string** |  |
| `$code` | **int** |  |
| `$previous` | **?\Throwable** |  |




**Throws:**

- [`BaseException`](../BaseException.md)



***

### __toString



```php
public __toString(): string
```












***


***
> Automatically generated on 2025-10-13
