***

# SecureHeaders





* Full name: `\Codefy\Framework\Http\Middleware\SecureHeaders\SecureHeaders`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### compiled



```php
protected bool $compiled
```






***

### headers



```php
protected array $headers
```






***

### nonces



```php
protected static array $nonces
```



* This property is **static**.


***

### config



```php
protected array $config
```






***

## Methods


### __construct



```php
public __construct(array $config = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$config` | **array** |  |





***

### headers



```php
public headers(): array
```












***

### compile



```php
protected compile(): void
```












***

### csp



```php
protected csp(): array
```












***

### hsts

Strict Transport Security.

```php
protected hsts(): array|string[]
```












***

### expectCT



```php
protected expectCT(): array
```












***

### clearSiteData

Generate Clear-Site-Data header.

```php
protected clearSiteData(): array
```












***

### permissionsPolicy



```php
protected permissionsPolicy(): array
```












***

### miscellaneous

Get Miscellaneous headers.

```php
protected miscellaneous(): array
```












***

### maxAge



```php
protected maxAge(): string
```












***

### reportUri

Get report-uri directive.

```php
protected reportUri(): string
```












***

### directive

Parse a specific permission policy value.

```php
protected directive(array $config): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$config` | **array** |  |





***

### origins

Get valid origins.

```php
protected origins(array $origins): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$origins` | **array** |  |





***

### nonce

Generate random nonce value for the current request.

```php
public static nonce(string $target = &#039;script&#039;): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$target` | **string** |  |




**Throws:**

- [`Exception`](../../../../../Exception.md)



***

### removeNonce

Remove a specific nonce value or flush all nonces for the given target.

```php
public static removeNonce(string|null $target = null, string|null $nonce = null): void
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$target` | **string&#124;null** |  |
| `$nonce` | **string&#124;null** |  |





***


***
> Automatically generated on 2025-10-13
