# CsrfTokenAware

***

* Full name: `\Codefy\Framework\Http\Middleware\Csrf\Traits\CsrfTokenAware`

## Properties

### salt

```php
protected ?string $salt
```

***
### isNew

```php
protected bool $isNew
```

***

## Methods

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

- [`BadFormatException`](../../../../../../Defuse/Crypto/Exception/BadFormatException.md)
- [`EnvironmentIsBrokenException`](../../../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)
- [`Exception`](../../../../../../Exception.md)
- [`WrongKeyOrModifiedCiphertextException`](../../../../../../Defuse/Crypto/Exception/WrongKeyOrModifiedCiphertextException.md)

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

- [`BadFormatException`](../../../../../../Defuse/Crypto/Exception/BadFormatException.md)
- [`EnvironmentIsBrokenException`](../../../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)
- [`Exception`](../../../../../../Exception.md)
- [`WrongKeyOrModifiedCiphertextException`](../../../../../../Defuse/Crypto/Exception/WrongKeyOrModifiedCiphertextException.md)

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

- [`BadFormatException`](../../../../../../Defuse/Crypto/Exception/BadFormatException.md)
- [`EnvironmentIsBrokenException`](../../../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)
- [`Exception`](../../../../../../Exception.md)
- [`TypeException`](../../../../../../Qubus/Exception/Data/TypeException.md)

***
