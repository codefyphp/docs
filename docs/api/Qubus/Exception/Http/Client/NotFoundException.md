***

# NotFoundException

Qubus Exception Class

This extends the default `BaseException` class to allow converting
exceptions to and from `Error` objects.

Unfortunately, because an `Error` object may contain multiple messages and error
codes, only the first message for the first error code in the instance will be
accessible through the exception's methods.

* Full name: `\Qubus\Exception\Http\Client\NotFoundException`
* Parent class: [`\Qubus\Exception\Exception`](../../Exception.md)




## Methods


### __construct



```php
public __construct(string $message = &#039;The requested entity cannot be found, this may be returned because &#039; . &#039;the entity is not accessible using requested credentials because of a recent state &#039; . &#039;change or because the entity cannot be found at all.&#039;, int $code = 404, ?\Throwable $previous = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$code` | **int** |  |
| `$previous` | **?\Throwable** |  |





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

- [`BaseException`](../../BaseException.md)



***

### __toString



```php
public __toString(): string
```












***


***
> Automatically generated on 2025-10-13
