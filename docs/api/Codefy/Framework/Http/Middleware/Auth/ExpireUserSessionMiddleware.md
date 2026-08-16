# ExpireUserSessionMiddleware

***

* Full name: `\Codefy\Framework\Http\Middleware\Auth\ExpireUserSessionMiddleware`
* This class implements:
  `MiddlewareInterface`

## Constants

| Constant            | Visibility | Type | Value                |
|---------------------|------------|------|----------------------|
| `SESSION_ATTRIBUTE` | public     |      | 'EXPIRE_USERSESSION' |

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

***
