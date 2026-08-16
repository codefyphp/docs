# ThrowableTransformAware

***

* Full name: `\Codefy\Framework\Traits\ThrowableTransformAware`

## Properties

### exceptionMap

A map of Throwable::class => callable(Throwable): HttpException

```php
protected array<class-string<\Throwable>,callable> $exceptionMap
```

***

## Methods

### mapException

Register a transformer for a specific Throwable class.

```php
public mapException(string $class, callable $transformer): void
```

Example:
$this->mapException(RecordsNotFoundException::class, fn($e) => new NotFoundHttpException('/x'));

**Parameters:**

| Parameter      | Type         | Description |
|----------------|--------------|-------------|
| `$class`       | **string**   |             |
| `$transformer` | **callable** |             |

***
### tryTransformException

Convert a Throwable into an HttpException if a mapping exists.

```php
protected tryTransformException(\Throwable $t): \Qubus\Exception\Http\HttpException|null
```

Otherwise, return null.

**Parameters:**

| Parameter | Type           | Description |
|-----------|----------------|-------------|
| `$t`      | **\Throwable** |             |

***
### transformToHttpException

Convert unknown exception to HttpException using best-available mapping.

```php
protected transformToHttpException(\Throwable $t): \Qubus\Exception\Http\HttpException
```

**Parameters:**

| Parameter | Type           | Description |
|-----------|----------------|-------------|
| `$t`      | **\Throwable** |             |

***
