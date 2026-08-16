# UserSessionMiddleware

***

* Full name: `\Codefy\Framework\Http\Middleware\Auth\UserSessionMiddleware`
* This class is marked as **final** and can't be subclassed
* This class implements:
  `MiddlewareInterface`
* This class is a **Final class**

## Constants

| Constant            | Visibility | Type | Value         |
|---------------------|------------|------|---------------|
| `SESSION_ATTRIBUTE` | public     |      | 'USERSESSION' |

## Properties

### configContainer

```php
protected \Qubus\Config\ConfigContainer $configContainer
```

***

### cookie

```php
protected \Qubus\Http\Cookies\Factory\HttpCookieFactory $cookie
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

- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)
- [`Exception`](../../../../../Exception.md)
- [`BadFormatException`](../../../../../Defuse/Crypto/Exception/BadFormatException.md)
- [`EnvironmentIsBrokenException`](../../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)

***

### cookieTtl

The cookie expiry.

```php
protected cookieTtl(\Psr\Http\Message\ServerRequestInterface $request): int
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

**Throws:**

- [`Exception`](../../../../../Exception.md)

***

### cookieName

The cookie name.

```php
protected cookieName(): string
```

**Throws:**

- [`Exception`](../../../../../Exception.md)

***

### userDetails

User details from request.

```php
protected userDetails(\Psr\Http\Message\ServerRequestInterface $request): mixed
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

***

### createCookie

Creates an HTTP cookie.

```php
protected createCookie(\Psr\Http\Message\ServerRequestInterface $request, \Psr\Http\Message\ResponseInterface $response, string $token): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter   | Type                                         | Description |
|-------------|----------------------------------------------|-------------|
| `$request`  | **\Psr\Http\Message\ServerRequestInterface** |             |
| `$response` | **\Psr\Http\Message\ResponseInterface**      |             |
| `$token`    | **string**                                   |             |

**Throws:**

- [`Exception`](../../../../../Exception.md)
- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)
- [`BadFormatException`](../../../../../Defuse/Crypto/Exception/BadFormatException.md)
- [`EnvironmentIsBrokenException`](../../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)

***

### isNew

```php
public isNew(\Psr\Http\Message\ServerRequestInterface $request): bool
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

**Throws:**

- [`Exception`](../../../../../Exception.md)

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

### tokensMatch

```php
private tokensMatch(\Psr\Http\Message\ServerRequestInterface $request): bool
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

**Throws:**

- [`Exception`](../../../../../Exception.md)

***

### fetchToken

```php
private fetchToken(\Psr\Http\Message\ServerRequestInterface $request): string
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

**Throws:**

- [`Exception`](../../../../../Exception.md)

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
