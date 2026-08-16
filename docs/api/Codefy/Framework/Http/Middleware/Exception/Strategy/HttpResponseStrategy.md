# HttpResponseStrategy

***

* Full name: `\Codefy\Framework\Http\Middleware\Exception\Strategy\HttpResponseStrategy`

## Methods

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

***
