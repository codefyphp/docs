***

# EmitterMiddleware





* Full name: `\Qubus\Http\Emitter\Middleware\EmitterMiddleware`
* This class implements:
[`\Psr\Http\Server\MiddlewareInterface`](../../../../Psr/Http/Server/MiddlewareInterface.md)



## Properties


### emitter



```php
private \Qubus\Http\Emitter\Emitter $emitter
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Http\Emitter\Emitter $emitter = new SapiEmitter()): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$emitter` | **\Qubus\Http\Emitter\Emitter** |  |





***

### process



```php
public process(\Psr\Http\Message\ServerRequestInterface $request, \Psr\Http\Server\RequestHandlerInterface $handler): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |
| `$handler` | **\Psr\Http\Server\RequestHandlerInterface** |  |





***


***
> Automatically generated on 2025-10-13
