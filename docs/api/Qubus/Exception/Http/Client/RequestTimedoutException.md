***

# RequestTimedoutException

Qubus Exception Class

This extends the default `BaseException` class to allow converting
exceptions to and from `Error` objects.

Unfortunately, because an `Error` object may contain multiple messages and error
codes, only the first message for the first error code in the instance will be
accessible through the exception's methods.

* Full name: `\Qubus\Exception\Http\Client\RequestTimedoutException`
* Parent class: [`\Qubus\Exception\Exception`](../../Exception.md)




## Methods


### __construct



```php
public __construct(string $message = &#039;A process further down the request chain failed to respond in time. &#039; . &#039;You can try again but you might get the same response if the server &#039; . &#039;load or the problem persists downstream.&#039;, int $code = 408, ?\Throwable $previous = null): mixed
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
