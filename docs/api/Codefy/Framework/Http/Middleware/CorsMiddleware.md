***

# CorsMiddleware





* Full name: `\Codefy\Framework\Http\Middleware\CorsMiddleware`
* This class implements:
[`\Psr\Http\Server\MiddlewareInterface`](../../../../Psr/Http/Server/MiddlewareInterface.md)



## Properties


### configContainer



```php
protected \Qubus\Config\ConfigContainer $configContainer
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Config\ConfigContainer $configContainer): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$configContainer` | **\Qubus\Config\ConfigContainer** |  |





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

- [`Exception`](../../../../Qubus/Exception/Exception.md)



***


***
> Automatically generated on 2025-10-13
