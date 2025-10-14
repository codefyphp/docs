***

# UserSessionMiddleware





* Full name: `\Codefy\Framework\Http\Middleware\Auth\UserSessionMiddleware`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Psr\Http\Server\MiddlewareInterface`](../../../../../Psr/Http/Server/MiddlewareInterface.md)
* This class is a **Final class**


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`SESSION_ATTRIBUTE`|public| |&#039;USERSESSION&#039;|

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





***


***
> Automatically generated on 2025-10-13
