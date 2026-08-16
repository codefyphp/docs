# EmitterMiddleware

***

* Full name: `\Qubus\Http\Emitter\Middleware\EmitterMiddleware`
* This class implements:
  `MiddlewareInterface`

## Properties

### emitter

```php
private \Qubus\Http\Emitter\Emitter $emitter
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Http\Emitter\Emitter $emitter = new \Qubus\Http\Emitter\SapiEmitter()): mixed
```

**Parameters:**

| Parameter  | Type                            | Description |
|------------|---------------------------------|-------------|
| `$emitter` | **\Qubus\Http\Emitter\Emitter** |             |

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

***
