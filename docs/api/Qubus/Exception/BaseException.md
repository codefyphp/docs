***

# BaseException





* Full name: `\Qubus\Exception\BaseException`
* Parent class: [`Exception`](../../Exception.md)
* This class implements:
[`\Stringable`](../../Stringable.md)



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
public __construct(?string $message = &#039;&#039;, int $code, ?\Throwable $previous = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **?string** |  |
| `$code` | **int** |  |
| `$previous` | **?\Throwable** |  |




**Throws:**

- [`BaseException`]()



***

### __toString



```php
public __toString(): string
```












***


***
> Automatically generated on 2025-10-13
