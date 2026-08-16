# ResponseCookieEncryptor

***

* Full name: `\Qubus\Http\Cookies\ResponseCookieEncryptor`

## Properties

### encryptor

```php
public \Qubus\Http\Encryption\Encryptor $encryptor
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
public __construct(\Qubus\Http\Encryption\Encryptor $encryptor, \Qubus\Http\Cookies\Validation\Validation $validation): mixed
```

**Parameters:**

| Parameter     | Type                                          | Description |
|---------------|-----------------------------------------------|-------------|
| `$encryptor`  | **\Qubus\Http\Encryption\Encryptor**          |             |
| `$validation` | **\Qubus\Http\Cookies\Validation\Validation** |             |

***

### resolveCookieNames

```php
private static resolveCookieNames(mixed $cookieNames): array
```

* This method is **static**.
**Parameters:**

| Parameter      | Type      | Description |
|----------------|-----------|-------------|
| `$cookieNames` | **mixed** |             |

***

### hasNoCookieNames

```php
private static hasNoCookieNames(array $cookieNames): bool
```

* This method is **static**.
**Parameters:**

| Parameter      | Type      | Description |
|----------------|-----------|-------------|
| `$cookieNames` | **array** |             |

***

### encrypt

```php
public encrypt(\Psr\Http\Message\ResponseInterface $response, mixed $cookieNames): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter      | Type                                    | Description |
|----------------|-----------------------------------------|-------------|
| `$response`    | **\Psr\Http\Message\ResponseInterface** |             |
| `$cookieNames` | **mixed**                               |             |

***

### encryptCookie

```php
private encryptCookie(\Qubus\Http\Cookies\SetCookies $setCookies, mixed $cookieName): \Qubus\Http\Cookies\SetCookies
```

**Parameters:**

| Parameter     | Type                               | Description |
|---------------|------------------------------------|-------------|
| `$setCookies` | **\Qubus\Http\Cookies\SetCookies** |             |
| `$cookieName` | **mixed**                          |             |

***
