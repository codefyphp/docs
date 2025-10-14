***

# Error





* Full name: `\Qubus\Error\Error`
* This class implements:
[`\Qubus\Error\Returnable`](./Returnable.md)



## Properties


### message



```php
protected string $message
```






***

### code



```php
protected int|string $code
```






***

### context



```php
protected $context
```






***

## Methods


### __construct



```php
public __construct(string $message = &#039;&#039;, int|string $code = &#039;&#039;, mixed $context = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$code` | **int&#124;string** |  |
| `$context` | **mixed** |  |





***

### getMessage



```php
public getMessage(): string
```












***

### getCode



```php
public getCode(): int
```












***

### getContext



```php
public getContext(): array
```












***

### __toString



```php
public __toString(): string
```












***


***
> Automatically generated on 2025-10-13
