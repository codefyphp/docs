***

# Kernel





* Full name: `\Codefy\Framework\Http\Kernel`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Codefy\Framework\Contracts\Http\Kernel`](../Contracts/Http/Kernel.md)
* This class is a **Final class**



## Properties


### codefy



```php
public \Codefy\Framework\Application $codefy
```






***

### router



```php
public \Qubus\Routing\Router $router
```






***

### bootstrappers



```php
protected array $bootstrappers
```






***

## Methods


### __construct



```php
public __construct(\Codefy\Framework\Application $codefy, \Qubus\Routing\Router $router): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$codefy` | **\Codefy\Framework\Application** |  |
| `$router` | **\Qubus\Routing\Router** |  |




**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)



***

### codefy

Get the CodefyPHP application instance.

```php
public codefy(): \Codefy\Framework\Application
```












***

### dispatchRouter



```php
protected dispatchRouter(?\Psr\Http\Message\ServerRequestInterface $request = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **?\Psr\Http\Message\ServerRequestInterface** |  |




**Throws:**

- [`Exception`](../../../Exception.md)



***

### handle

Handle a server request.

```php
public handle(\Psr\Http\Message\ServerRequestInterface $request): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |




**Throws:**

- [`Exception`](../../../Exception.md)



***

### boot

Kernel boots the application.

```php
public boot(?\Psr\Http\Message\ServerRequestInterface $request = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **?\Psr\Http\Message\ServerRequestInterface** |  |




**Throws:**

- [`Exception`](../../../Exception.md)



***

### bootstrappers

Get the bootstrappers.

```php
protected bootstrappers(): string[]
```












***

### registerErrorHandler



```php
protected registerErrorHandler(): \Qubus\Error\Handlers\ErrorHandler
```











**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)



***


***
> Automatically generated on 2025-10-13
