# JsonHttpExceptionMiddleware

***

* Full name: `\Codefy\Framework\Http\Middleware\Exception\JsonHttpExceptionMiddleware`
* This class implements:
  `MiddlewareInterface`

## Properties

### app

```php
protected \Codefy\Framework\Application $app
```

***

## Methods

### __construct

```php
public __construct(\Codefy\Framework\Application $app): mixed
```

**Parameters:**

| Parameter | Type                              | Description |
|-----------|-----------------------------------|-------------|
| `$app`    | **\Codefy\Framework\Application** |             |

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

- [`ReflectionException`](../../../../../ReflectionException.md)
- [`Exception`](../../../../../Exception.md)

***

## Inherited methods

### normalizeStatusCode

```php
protected normalizeStatusCode(int $code): int
```

**Parameters:**

| Parameter | Type    | Description |
|-----------|---------|-------------|
| `$code`   | **int** |             |

***

### isJson

```php
protected isJson(\Psr\Http\Message\ServerRequestInterface $request): bool
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

***

### getSafeReferrer

```php
protected getSafeReferrer(\Psr\Http\Message\ServerRequestInterface $request): string
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

***

### shouldRenderView

```php
protected shouldRenderView(): bool
```

**Throws:**

- [`Exception`](../../../../../Qubus/Exception/Exception.md)

***

### logException

```php
protected logException(\Throwable $t): void
```

**Parameters:**

| Parameter | Type           | Description |
|-----------|----------------|-------------|
| `$t`      | **\Throwable** |             |

**Throws:**

- [`ReflectionException`](../../../../../ReflectionException.md)

***
