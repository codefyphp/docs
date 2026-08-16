# CsrfTokenMiddleware

***

* Full name: `\Codefy\Framework\Http\Middleware\Csrf\CsrfTokenMiddleware`
* This class implements:
  `MiddlewareInterface`

## Constants

| Constant                 | Visibility | Type | Value        |
|--------------------------|------------|------|--------------|
| `CSRF_SESSION_ATTRIBUTE` | public     |      | 'CSRF_TOKEN' |

## Properties

### current

```php
public static \Codefy\Framework\Http\Middleware\Csrf\CsrfTokenMiddleware $current
```

* This property is **static**.

***

### token

```php
private ?string $token
```

***

### configContainer

```php
protected \Qubus\Config\ConfigContainer $configContainer
```

***

### cookie

```php
public \Qubus\Http\Cookies\Factory\HttpCookieFactory $cookie
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Config\ConfigContainer $configContainer, \Qubus\Http\Cookies\Factory\HttpCookieFactory $cookie): mixed
```

**Parameters:**

| Parameter          | Type                                              | Description |
|--------------------|---------------------------------------------------|-------------|
| `$configContainer` | **\Qubus\Config\ConfigContainer**                 |             |
| `$cookie`          | **\Qubus\Http\Cookies\Factory\HttpCookieFactory** |             |

***

### getField

```php
public static getField(): string
```

* This method is **static**.
**Throws:**

- [`Exception`](../../../../../Qubus/Exception/Exception.md)

***

### getFieldAttr

```php
public getFieldAttr(): string
```

**Throws:**

- [`Exception`](../../../../../Qubus/Exception/Exception.md)

***

### process

```php
public process(\Psr\Http\Message\ServerRequestInterface $request, \Psr\Http\Server\RequestHandlerInterface $handler): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |
| `$handler` | **\Psr\Http\Server\RequestHandlerInterface** |             |

**Throws:**

- [`Exception`](../../../../../Qubus/Exception/Exception.md)
- [`BadFormatException`](../../../../../Defuse/Crypto/Exception/BadFormatException.md)
- [`EnvironmentIsBrokenException`](../../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)
- [`WrongKeyOrModifiedCiphertextException`](../../../../../Defuse/Crypto/Exception/WrongKeyOrModifiedCiphertextException.md)

***

## Inherited methods

### sign

Sign the value.

```php
protected sign(string $value): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$value`  | **string** |             |

**Throws:**

- [`EnvironmentIsBrokenException`](../../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)
- [`BadFormatException`](../../../../../Defuse/Crypto/Exception/BadFormatException.md)

***

### unsign

Unsign the value.

```php
protected unsign(string $value): string
```

**Parameters:**

| Parameter | Type       | Description      |
|-----------|------------|------------------|
| `$value`  | **string** | Encrypted value. |

**Return Value:**

Return the value if signature is valid.

**Throws:**

- [`BadFormatException`](../../../../../Defuse/Crypto/Exception/BadFormatException.md)
- [`EnvironmentIsBrokenException`](../../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)
- [`WrongKeyOrModifiedCiphertextException`](../../../../../Defuse/Crypto/Exception/WrongKeyOrModifiedCiphertextException.md)

***

### compareTokens

```php
protected compareTokens(string $knownString, string $userString): bool
```

**Parameters:**

| Parameter      | Type       | Description |
|----------------|------------|-------------|
| `$knownString` | **string** |             |
| `$userString`  | **string** |             |

***

### generateToken

```php
protected generateToken(): string
```

***

### prepareToken

```php
protected prepareToken(\Psr\Http\Message\ServerRequestInterface $request): string
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

**Throws:**

- [`BadFormatException`](../../../../../Defuse/Crypto/Exception/BadFormatException.md)
- [`EnvironmentIsBrokenException`](../../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)
- [`Exception`](../../../../../Exception.md)
- [`WrongKeyOrModifiedCiphertextException`](../../../../../Defuse/Crypto/Exception/WrongKeyOrModifiedCiphertextException.md)

***

### getTokenFromCookie

Get the token from the request cookie if it's present.

```php
private getTokenFromCookie(array $cookies): string|null
```

Decrypt the cookie token value using the app crypto key.

Return null if the cookie is missing or if the decryption fails.

**Parameters:**

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `$cookies` | **array** |             |

**Throws:**

- [`BadFormatException`](../../../../../Defuse/Crypto/Exception/BadFormatException.md)
- [`EnvironmentIsBrokenException`](../../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)
- [`Exception`](../../../../../Exception.md)
- [`WrongKeyOrModifiedCiphertextException`](../../../../../Defuse/Crypto/Exception/WrongKeyOrModifiedCiphertextException.md)

***

### createCookie

Create CSRF cookie to store the encrypted token value.

```php
private createCookie(\Psr\Http\Message\ResponseInterface $response, string $token): \Psr\Http\Message\ResponseInterface
```

Encrypt the value for better security (in case of XSS attack).

**Parameters:**

| Parameter   | Type                                    | Description |
|-------------|-----------------------------------------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |             |
| `$token`    | **string**                              |             |

**Throws:**

- [`BadFormatException`](../../../../../Defuse/Crypto/Exception/BadFormatException.md)
- [`EnvironmentIsBrokenException`](../../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)
- [`Exception`](../../../../../Exception.md)
- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)

***
