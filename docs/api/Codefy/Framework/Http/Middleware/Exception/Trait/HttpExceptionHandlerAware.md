# HttpExceptionHandlerAware

***

* Full name: `\Codefy\Framework\Http\Middleware\Exception\Trait\HttpExceptionHandlerAware`

## Methods

### handleHttpException

```php
protected handleHttpException(\Qubus\Exception\Http\HttpException|\Qubus\Exception\Http\Psr7Exception $e, \Psr\Http\Message\ServerRequestInterface $request): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter  | Type                                                                         | Description |
|------------|------------------------------------------------------------------------------|-------------|
| `$e`       | **\Qubus\Exception\Http\HttpException\|\Qubus\Exception\Http\Psr7Exception** |             |
| `$request` | **\Psr\Http\Message\ServerRequestInterface**                                 |             |

**Throws:**

- [`ReflectionException`](../../../../../../ReflectionException.md)
- [`TypeException`](../../../../../../Qubus/Exception/Data/TypeException.md)
- [`Exception`](../../../../../../Exception.md)

***
### handleUnknownException

```php
protected handleUnknownException(\Throwable $t, \Psr\Http\Message\ServerRequestInterface $request): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$t`       | **\Throwable**                               |             |
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

**Throws:**

- [`NotFoundException`](../../../../../../Qubus/Exception/Http/Client/NotFoundException.md)
- [`ReflectionException`](../../../../../../ReflectionException.md)
- [`TypeException`](../../../../../../Qubus/Exception/Data/TypeException.md)
- [`Exception`](../../../../../../Exception.md)

***
