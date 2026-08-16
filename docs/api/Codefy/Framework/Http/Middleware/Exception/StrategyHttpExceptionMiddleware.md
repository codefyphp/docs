# StrategyHttpExceptionMiddleware

***

* Full name: `\Codefy\Framework\Http\Middleware\Exception\StrategyHttpExceptionMiddleware`
* This class implements:
  `MiddlewareInterface`

## Properties

### handler

```php
protected \Codefy\Framework\Http\Middleware\Exception\ExceptionHandler $handler
```

***

## Methods

### __construct

```php
public __construct(\Codefy\Framework\Http\Middleware\Exception\ExceptionHandler $handler): mixed
```

**Parameters:**

| Parameter  | Type                                                             | Description |
|------------|------------------------------------------------------------------|-------------|
| `$handler` | **\Codefy\Framework\Http\Middleware\Exception\ExceptionHandler** |             |

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

- [`Exception`](../../../../../Exception.md)

***
