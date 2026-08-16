# HttpExceptionRenderAware

***

* Full name: `\Codefy\Framework\Http\Middleware\Exception\Trait\HttpExceptionRenderAware`

## Properties

### errorView

```php
protected \Codefy\Framework\View\ErrorViewRenderer $errorView
```

***

## Methods

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
