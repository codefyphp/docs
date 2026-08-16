# EncryptCookiesMiddleware

***

* Full name: `\Qubus\Http\Cookies\Middleware\EncryptCookiesMiddleware`
* This class implements:
  `MiddlewareInterface`

## Properties

### bypass

A list of cookie names not to encrypt/decrypt.

```php
protected array<int,string> $bypass
```

***

### key

The key with which to encrypt cookies.

```php
protected \Defuse\Crypto\Key|null $key
```

***

## Methods

### __construct

Create a new instance of the middleware

```php
public __construct(\Defuse\Crypto\Key $cryptoKey, array<int,string> $bypassCookieNames = []): mixed
```

**Parameters:**

| Parameter            | Type                   | Description |
|----------------------|------------------------|-------------|
| `$cryptoKey`         | **\Defuse\Crypto\Key** |             |
| `$bypassCookieNames` | **array<int,string>**  |             |

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

- [`TypeException`](../../../Exception/Data/TypeException.md)

***

### encrypt

```php
public encrypt(\Qubus\Http\Cookies\SetCookieCollection $setCookie): \Qubus\Http\Cookies\SetCookieCollection
```

**Parameters:**

| Parameter    | Type                                        | Description |
|--------------|---------------------------------------------|-------------|
| `$setCookie` | **\Qubus\Http\Cookies\SetCookieCollection** |             |

**Throws:**

- [`EnvironmentIsBrokenException`](../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)

***

### decrypt

```php
public decrypt(\Qubus\Http\Cookies\CookieCollection $cookie): \Qubus\Http\Cookies\CookieCollection
```

**Parameters:**

| Parameter | Type                                     | Description |
|-----------|------------------------------------------|-------------|
| `$cookie` | **\Qubus\Http\Cookies\CookieCollection** |             |

***
