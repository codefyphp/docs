# AuthenticationMiddleware

***

* Full name: `\Codefy\Framework\Http\Middleware\Auth\AuthenticationMiddleware`
* This class is marked as **final** and can't be subclassed
* This class implements:
  `MiddlewareInterface`
* This class is a **Final class**

## Constants

| Constant         | Visibility | Type | Value         |
|------------------|------------|------|---------------|
| `AUTH_ATTRIBUTE` | public     |      | 'USERSESSION' |

## Properties

### auth

```php
protected \Codefy\Framework\Auth\Sentinel $auth
```

***

## Methods

### __construct

```php
public __construct(\Codefy\Framework\Auth\Sentinel $auth): mixed
```

**Parameters:**

| Parameter | Type                                | Description |
|-----------|-------------------------------------|-------------|
| `$auth`   | **\Codefy\Framework\Auth\Sentinel** |             |

***

### process

{@inheritDoc}

```php
public process(\Psr\Http\Message\ServerRequestInterface $request, \Psr\Http\Server\RequestHandlerInterface $handler): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |
| `$handler` | **\Psr\Http\Server\RequestHandlerInterface** |             |

***
