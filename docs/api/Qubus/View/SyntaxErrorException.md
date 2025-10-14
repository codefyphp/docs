***

# SyntaxErrorException





* Full name: `\Qubus\View\SyntaxErrorException`
* Parent class: [`Exception`](../Exception/Exception.md)
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### token



```php
protected \Qubus\View\Token $token
```






***

### path



```php
protected string $path
```






***

## Methods


### __construct



```php
public __construct(string $message, \Qubus\View\Token $token): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$token` | **\Qubus\View\Token** |  |




**Throws:**

- [`BaseException`](../Exception/BaseException.md)



***

### setTemplateFile



```php
public setTemplateFile(mixed $path): \Qubus\View\SyntaxErrorException
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **mixed** |  |





***

### getTemplateFile



```php
public getTemplateFile(): string
```












***

### __toString



```php
public __toString(): string
```












***

### setMessage



```php
public setMessage(mixed $message): \Qubus\View\SyntaxErrorException
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **mixed** |  |





***

### getToken



```php
public getToken(): \Qubus\View\Token
```












***


***
> Automatically generated on 2025-10-13
