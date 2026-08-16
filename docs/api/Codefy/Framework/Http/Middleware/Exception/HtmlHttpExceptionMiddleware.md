# HtmlHttpExceptionMiddleware

***

* Full name: `\Codefy\Framework\Http\Middleware\Exception\HtmlHttpExceptionMiddleware`
* This class implements:
  `MiddlewareInterface`

## Properties

### app

```php
protected \Codefy\Framework\Application $app
```

***

### errorView

```php
protected \Codefy\Framework\View\ErrorViewRenderer $errorView
```

***

## Methods

### __construct

```php
public __construct(\Codefy\Framework\Application $app, \Codefy\Framework\View\ErrorViewRenderer $errorView): mixed
```

**Parameters:**

| Parameter    | Type                                         | Description |
|--------------|----------------------------------------------|-------------|
| `$app`       | **\Codefy\Framework\Application**            |             |
| `$errorView` | **\Codefy\Framework\View\ErrorViewRenderer** |             |

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

### renderErrorView

```php
protected renderErrorView(\Throwable $t): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter | Type           | Description |
|-----------|----------------|-------------|
| `$t`      | **\Throwable** |             |

**Throws:**

- [`NotFoundException`](../../../../../Qubus/Exception/Http/Client/NotFoundException.md)
- [`Exception`](../../../../../Exception.md)

***

### redirectWithHttpError

```php
protected redirectWithHttpError(\Psr\Http\Message\ServerRequestInterface $request, \Qubus\Exception\Http\HttpException|\Qubus\Exception\Http\Psr7Exception $e): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter  | Type                                                                         | Description |
|------------|------------------------------------------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface**                                 |             |
| `$e`       | **\Qubus\Exception\Http\HttpException\|\Qubus\Exception\Http\Psr7Exception** |             |

**Throws:**

- [`Exception`](../../../../../Exception.md)

***

### jsonHttpErrorResponse

```php
protected jsonHttpErrorResponse(\Qubus\Exception\Http\Psr7Exception $e): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$e`      | **\Qubus\Exception\Http\Psr7Exception** |             |

**Throws:**

- [`Exception`](../../../../../Exception.md)

***

### redirectWithInternalError

```php
protected redirectWithInternalError(\Psr\Http\Message\ServerRequestInterface $request): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

***

### jsonInternalErrorResponse

```php
protected jsonInternalErrorResponse(\Throwable $t): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter | Type           | Description |
|-----------|----------------|-------------|
| `$t`      | **\Throwable** |             |

**Throws:**

- [`Exception`](../../../../../Exception.md)

***
