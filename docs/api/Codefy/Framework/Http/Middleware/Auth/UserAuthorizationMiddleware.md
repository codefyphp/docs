***

# UserAuthorizationMiddleware





* Full name: `\Codefy\Framework\Http\Middleware\Auth\UserAuthorizationMiddleware`
* This class implements:
[`\Psr\Http\Server\MiddlewareInterface`](../../../../../Psr/Http/Server/MiddlewareInterface.md)


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`HEADER_HTTP_STATUS_CODE`|public| |&#039;AUTH_STATUS_CODE&#039;|

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

### responseFactory



```php
protected \Psr\Http\Message\ResponseFactoryInterface $responseFactory
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Config\ConfigContainer $configContainer, \Qubus\Http\Session\SessionService $sessionService, \Psr\Http\Message\ResponseFactoryInterface $responseFactory): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$configContainer` | **\Qubus\Config\ConfigContainer** |  |
| `$sessionService` | **\Qubus\Http\Session\SessionService** |  |
| `$responseFactory` | **\Psr\Http\Message\ResponseFactoryInterface** |  |





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

### isLoggedIn



```php
private isLoggedIn(\Psr\Http\Message\ServerRequestInterface $request): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |




**Throws:**

- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)

- [`Exception`](../../../../../Exception.md)



***


***
> Automatically generated on 2025-10-13
