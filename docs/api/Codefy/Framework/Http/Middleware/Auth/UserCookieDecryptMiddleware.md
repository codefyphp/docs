# UserCookieDecryptMiddleware

***

* Full name: `\Codefy\Framework\Http\Middleware\Auth\UserCookieDecryptMiddleware`
* This class implements:
  `MiddlewareInterface`

## Constants

| Constant      | Visibility | Type | Value        |
|---------------|------------|------|--------------|
| `USER_COOKIE` | public     |      | 'auth.token' |

## Properties

### configContainer

```php
private \Qubus\Config\ConfigContainer $configContainer
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Config\ConfigContainer $configContainer): mixed
```

**Parameters:**

| Parameter          | Type                              | Description |
|--------------------|-----------------------------------|-------------|
| `$configContainer` | **\Qubus\Config\ConfigContainer** |             |

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

***

### decryptCookie

Decrypt the cookie safely. Return null on any failure.

```php
private decryptCookie(string $encrypted): ?string
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$encrypted` | **string** |             |

**Throws:**

- [`ReflectionException`](../../../../../ReflectionException.md)

***
