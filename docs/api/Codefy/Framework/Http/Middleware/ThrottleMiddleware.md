# ThrottleMiddleware

***

* Full name: `\Codefy\Framework\Http\Middleware\ThrottleMiddleware`
* This class implements:
  `MiddlewareInterface`

## Properties

### configContainer

```php
protected \Qubus\Config\ConfigContainer $configContainer
```

***

### rateLimiter

```php
protected \Codefy\Framework\Http\Throttle\RateLimiter $rateLimiter
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Config\ConfigContainer $configContainer, \Codefy\Framework\Http\Throttle\RateLimiter $rateLimiter): mixed
```

**Parameters:**

| Parameter          | Type                                            | Description |
|--------------------|-------------------------------------------------|-------------|
| `$configContainer` | **\Qubus\Config\ConfigContainer**               |             |
| `$rateLimiter`     | **\Codefy\Framework\Http\Throttle\RateLimiter** |             |

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

- [`Exception`](../../../../Exception.md)

***
