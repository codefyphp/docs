***

# ContextErrorException





* Full name: `\Qubus\Error\Exceptions\ContextErrorException`
* Parent class: [`ErrorException`](../../../ErrorException.md)



## Properties


### context



```php
protected array $context
```






***

## Methods


### __construct



```php
public __construct(string $message, int $code, int $severity, ?string $filename = null, ?int $lineno = null, array $context = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$code` | **int** |  |
| `$severity` | **int** |  |
| `$filename` | **?string** |  |
| `$lineno` | **?int** |  |
| `$context` | **array** |  |





***

### getContext



```php
public getContext(): array
```












***


***
> Automatically generated on 2025-10-13
