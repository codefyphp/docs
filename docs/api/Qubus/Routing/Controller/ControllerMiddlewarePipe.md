***

# ControllerMiddlewarePipe





* Full name: `\Qubus\Routing\Controller\ControllerMiddlewarePipe`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### middleware



```php
protected array|\Psr\Http\Server\MiddlewareInterface|string $middleware
```






***

### options



```php
protected \Qubus\Routing\Controller\ControllerMiddlewareOptions $options
```






***

## Methods


### __construct

Constructor

```php
public __construct(\Psr\Http\Server\MiddlewareInterface|array|string $middleware, \Qubus\Routing\Controller\ControllerMiddlewareOptions $options): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$middleware` | **\Psr\Http\Server\MiddlewareInterface&#124;array&#124;string** |  |
| `$options` | **\Qubus\Routing\Controller\ControllerMiddlewareOptions** |  |





***

### middleware

Get the Middleware.

```php
public middleware(): \Psr\Http\Server\MiddlewareInterface|array|string
```












***

### options

Get the ControllerMiddlewareOptions.

```php
public options(): \Qubus\Routing\Controller\ControllerMiddlewareOptions
```












***

### excludedForMethod

Is a specific method excluded by the options set on this object.

```php
public excludedForMethod(string $method): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$method` | **string** |  |





***


***
> Automatically generated on 2025-10-13
