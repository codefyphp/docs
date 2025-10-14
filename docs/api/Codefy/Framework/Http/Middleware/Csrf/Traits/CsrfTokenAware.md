***

# CsrfTokenAware





* Full name: `\Codefy\Framework\Http\Middleware\Csrf\Traits\CsrfTokenAware`




## Methods


### generateToken



```php
protected generateToken(): string
```











**Throws:**

- [`Exception`](../../../../../../Qubus/Exception/Exception.md)



***

### prepareToken



```php
protected prepareToken(\Qubus\Http\Session\HttpSession $session): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$session` | **\Qubus\Http\Session\HttpSession** |  |




**Throws:**

- [`Exception`](../../../../../../Qubus/Exception/Exception.md)



***

### hashEquals



```php
protected hashEquals(string $knownString, string $userString): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$knownString` | **string** |  |
| `$userString` | **string** |  |




**Throws:**

- [`Exception`](../../../../../../Qubus/Exception/Exception.md)



***

***
> Automatically generated on 2025-10-13

