# HtmlHttpResponseStrategy

***

* Full name: `\Codefy\Framework\Http\Middleware\Exception\Strategy\HtmlHttpResponseStrategy`
* This class implements:
  [`\Codefy\Framework\Http\Middleware\Exception\Strategy\HttpResponseStrategy`](./HttpResponseStrategy.md)

## Properties

### errorView

```php
protected \Codefy\Framework\View\ErrorViewRenderer $errorView
```

***

### app

```php
protected \Codefy\Framework\Application $app
```

***

## Methods

### __construct

```php
public __construct(\Codefy\Framework\View\ErrorViewRenderer $errorView, \Codefy\Framework\Application $app): mixed
```

**Parameters:**

| Parameter    | Type                                         | Description |
|--------------|----------------------------------------------|-------------|
| `$errorView` | **\Codefy\Framework\View\ErrorViewRenderer** |             |
| `$app`       | **\Codefy\Framework\Application**            |             |

***

### supports

```php
public supports(\Throwable $e, \Psr\Http\Message\ServerRequestInterface $request): bool
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$e`       | **\Throwable**                               |             |
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

***

### createResponse

```php
public createResponse(\Throwable $e, \Psr\Http\Message\ServerRequestInterface $request): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$e`       | **\Throwable**                               |             |
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

**Throws:**

- [`NotFoundException`](../../../../../../Qubus/Exception/Http/Client/NotFoundException.md)
- [`Exception`](../../../../../../Exception.md)

***

## Inherited methods

### renderErrorView

```php
protected renderErrorView(\Throwable $t): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter | Type           | Description |
|-----------|----------------|-------------|
| `$t`      | **\Throwable** |             |

**Throws:**

- [`NotFoundException`](../../../../../../Qubus/Exception/Http/Client/NotFoundException.md)
- [`Exception`](../../../../../../Exception.md)

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

- [`Exception`](../../../../../../Exception.md)

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

- [`Exception`](../../../../../../Exception.md)

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

- [`Exception`](../../../../../../Exception.md)

***

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

- [`Exception`](../../../../../../Qubus/Exception/Exception.md)

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

- [`ReflectionException`](../../../../../../ReflectionException.md)

***
