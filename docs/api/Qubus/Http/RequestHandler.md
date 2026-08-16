# RequestHandler

***

* Full name: `\Qubus\Http\RequestHandler`
* This class is marked as **final** and can't be subclassed
* This class implements:
  `RequestHandlerInterface`
* This class is a **Final class**

## Constants

| Constant        | Visibility | Type | Value |
|-----------------|------------|------|-------|
| `RESPONSE_CODE` | public     |      | 200   |

## Properties

### responseFactory

```php
private \Psr\Http\Message\ResponseFactoryInterface $responseFactory
```

***

### middlewares

```php
private \Psr\Http\Server\MiddlewareInterface[] $middlewares
```

***

## Methods

### __construct

```php
public __construct(\Psr\Http\Message\ResponseFactoryInterface $responseFactory, array $middlewares = []): mixed
```

**Parameters:**

| Parameter          | Type                                           | Description |
|--------------------|------------------------------------------------|-------------|
| `$responseFactory` | **\Psr\Http\Message\ResponseFactoryInterface** |             |
| `$middlewares`     | **array**                                      |             |

***

### handle

```php
public handle(\Psr\Http\Message\ServerRequestInterface $request): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

***
