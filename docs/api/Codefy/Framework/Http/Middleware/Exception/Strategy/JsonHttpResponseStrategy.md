# JsonHttpResponseStrategy

***

* Full name: `\Codefy\Framework\Http\Middleware\Exception\Strategy\JsonHttpResponseStrategy`
* This class is marked as **final** and can't be subclassed
* This class implements:
  [`\Codefy\Framework\Http\Middleware\Exception\Strategy\HttpResponseStrategy`](./HttpResponseStrategy.md)
* This class is a **Final class**

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

- [`Exception`](../../../../../../Exception.md)

***
