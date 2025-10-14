***

# SessionMiddleware





* Full name: `\Qubus\Http\Session\Middleware\SessionMiddleware`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Psr\Http\Server\MiddlewareInterface`](../../../../Psr/Http/Server/MiddlewareInterface.md)
* This class is a **Final class**


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`SESSION_ATTRIBUTE`|public| |&#039;qubus.session&#039;|

## Properties


### sessionService



```php
public \Qubus\Http\Session\SessionService $sessionService
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Http\Session\SessionService $sessionService): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$sessionService` | **\Qubus\Http\Session\SessionService** |  |





***

### process

{@inheritDoc}

```php
public process(\Psr\Http\Message\ServerRequestInterface $request, \Psr\Http\Server\RequestHandlerInterface $handler): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |
| `$handler` | **\Psr\Http\Server\RequestHandlerInterface** |  |




**Throws:**

- [`Exception`](../../../Exception/Exception.md)

- [`TypeException`](../../../Exception/Data/TypeException.md)

- [`InvalidArgumentException`](../../../../InvalidArgumentException.md)

- [`Exception`](../../../../Exception.md)



***


***
> Automatically generated on 2025-10-13
