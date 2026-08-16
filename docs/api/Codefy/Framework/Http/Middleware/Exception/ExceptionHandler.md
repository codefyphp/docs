# ExceptionHandler

***

* Full name: `\Codefy\Framework\Http\Middleware\Exception\ExceptionHandler`

## Properties

### strategies

```php
protected array $strategies
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
public __construct(class-string<\Codefy\Framework\Http\Middleware\Exception\Strategy\HttpResponseStrategy>[]|\Codefy\Framework\Http\Middleware\Exception\Strategy\HttpResponseStrategy[] $strategies, \Codefy\Framework\Application $app): mixed
```

**Parameters:**

| Parameter     | Type                                                                                                                                                                       | Description |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| `$strategies` | **class-string<\Codefy\Framework\Http\Middleware\Exception\Strategy\HttpResponseStrategy>[]\|\Codefy\Framework\Http\Middleware\Exception\Strategy\HttpResponseStrategy[]** |             |
| `$app`        | **\Codefy\Framework\Application**                                                                                                                                          |             |

***

### handle

```php
public handle(\Throwable $e, \Psr\Http\Message\ServerRequestInterface $request): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$e`       | **\Throwable**                               |             |
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

**Throws:**

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
