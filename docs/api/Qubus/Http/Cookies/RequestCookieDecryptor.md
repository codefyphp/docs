***

# RequestCookieDecryptor





* Full name: `\Qubus\Http\Cookies\RequestCookieDecryptor`



## Properties


### decryptor



```php
public \Qubus\Http\Encryption\Decryptor $decryptor
```






***

### validation



```php
public \Qubus\Http\Cookies\Validation\Validation $validation
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Http\Encryption\Decryptor $decryptor, \Qubus\Http\Cookies\Validation\Validation $validation): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$decryptor` | **\Qubus\Http\Encryption\Decryptor** |  |
| `$validation` | **\Qubus\Http\Cookies\Validation\Validation** |  |





***

### resolveCookieNames



```php
private static resolveCookieNames(mixed $cookieNames): array
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$cookieNames` | **mixed** |  |





***

### hasNoCookieNames



```php
private static hasNoCookieNames(array $cookieNames): bool
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$cookieNames` | **array** |  |





***

### decrypt



```php
public decrypt(\Psr\Http\Message\RequestInterface $request, mixed $cookieNames): \Psr\Http\Message\RequestInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\RequestInterface** |  |
| `$cookieNames` | **mixed** |  |





***

### decryptCookie



```php
private decryptCookie(\Qubus\Http\Cookies\Cookies $cookies, mixed $cookieName): \Qubus\Http\Cookies\Cookies
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$cookies` | **\Qubus\Http\Cookies\Cookies** |  |
| `$cookieName` | **mixed** |  |





***


***
> Automatically generated on 2025-10-13
