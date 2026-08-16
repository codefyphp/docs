# ContentSecurityPolicyMiddleware

***

* Full name: `\Codefy\Framework\Http\Middleware\SecureHeaders\ContentSecurityPolicyMiddleware`
* This class implements:
  `MiddlewareInterface`

## Properties

### configContainer

```php
protected \Qubus\Config\ConfigContainer $configContainer
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
