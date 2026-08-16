# ContentCacheMiddleware

***

* Full name: `\Codefy\Framework\Http\Middleware\ContentCacheMiddleware`
* This class implements:
  `MiddlewareInterface`

## Properties

### cacheItemPool

```php
protected \Psr\Cache\CacheItemPoolInterface $cacheItemPool
```

***

## Methods

### __construct

```php
public __construct(\Psr\Cache\CacheItemPoolInterface $cacheItemPool): mixed
```

**Parameters:**

| Parameter        | Type                                  | Description |
|------------------|---------------------------------------|-------------|
| `$cacheItemPool` | **\Psr\Cache\CacheItemPoolInterface** |             |

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

- [`InvalidArgumentException`](../../../../Psr/Cache/InvalidArgumentException.md)

***

### buildResponse

```php
protected buildResponse(mixed $html, \Psr\Http\Message\ResponseInterface $response): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter   | Type                                    | Description |
|-------------|-----------------------------------------|-------------|
| `$html`     | **mixed**                               |             |
| `$response` | **\Psr\Http\Message\ResponseInterface** |             |

***

### createKeyFromRequest

```php
protected createKeyFromRequest(\Psr\Http\Message\RequestInterface $request): string
```

**Parameters:**

| Parameter  | Type                                   | Description |
|------------|----------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\RequestInterface** |             |

***

### getCachedResponseHtml

```php
protected getCachedResponseHtml(\Psr\Http\Message\RequestInterface $request): mixed
```

**Parameters:**

| Parameter  | Type                                   | Description |
|------------|----------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\RequestInterface** |             |

**Throws:**

- [`InvalidArgumentException`](../../../../Psr/Cache/InvalidArgumentException.md)

***

### cacheResponse

```php
protected cacheResponse(\Psr\Http\Message\RequestInterface $request, \Psr\Http\Message\ResponseInterface $response): void
```

**Parameters:**

| Parameter   | Type                                    | Description |
|-------------|-----------------------------------------|-------------|
| `$request`  | **\Psr\Http\Message\RequestInterface**  |             |
| `$response` | **\Psr\Http\Message\ResponseInterface** |             |

***
