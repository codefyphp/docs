***

# ExpireUserSessionMiddleware





* Full name: `\Codefy\Framework\Http\Middleware\Auth\ExpireUserSessionMiddleware`
* This class implements:
[`\Psr\Http\Server\MiddlewareInterface`](../../../../../Psr/Http/Server/MiddlewareInterface.md)


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`SESSION_ATTRIBUTE`|public| |&#039;EXPIRE_USERSESSION&#039;|

## Properties


### configContainer



```php
protected \Qubus\Config\ConfigContainer $configContainer
```






***

### sessionService



```php
protected \Qubus\Http\Session\SessionService $sessionService
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Config\ConfigContainer $configContainer, \Qubus\Http\Session\SessionService $sessionService): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$configContainer` | **\Qubus\Config\ConfigContainer** |  |
| `$sessionService` | **\Qubus\Http\Session\SessionService** |  |





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




**Throws:**

- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)

- [`Exception`](../../../../../Exception.md)



***


***
> Automatically generated on 2025-10-13
