***

# CsrfSession





* Full name: `\Codefy\Framework\Http\Middleware\Csrf\CsrfSession`
* This class implements:
[`\Qubus\Http\Session\SessionEntity`](../../../../../Qubus/Http/Session/SessionEntity.md)



## Properties


### csrfToken



```php
public ?string $csrfToken
```






***

## Methods


### withCsrfToken



```php
public withCsrfToken(?string $csrfToken = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$csrfToken` | **?string** |  |





***

### equals



```php
public equals(string $token): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$token` | **string** |  |





***

### csrfToken



```php
public csrfToken(): string|null
```












***

### clear



```php
public clear(): void
```












***

### isEmpty



```php
public isEmpty(): bool
```












***


***
> Automatically generated on 2025-10-13
