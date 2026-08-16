# HttpExceptionUtilityAware

***

* Full name: `\Codefy\Framework\Http\Middleware\Exception\Trait\HttpExceptionUtilityAware`

## Methods

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
