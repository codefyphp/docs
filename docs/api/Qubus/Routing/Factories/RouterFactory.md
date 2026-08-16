# RouterFactory

***

* Full name: `\Qubus\Routing\Factories\RouterFactory`
* This class is marked as **final** and can't be subclassed
* This class implements:
  [`\Qubus\Routing\Factories\RouterableFactory`](./RouterableFactory.md)
* This class is a **Final class**

## Properties

### routeCollector

```php
protected static \Qubus\Routing\Route\RouteCollector $routeCollector
```

* This property is **static**.

***

### container

```php
protected static ?\Psr\Container\ContainerInterface $container
```

* This property is **static**.

***

### responseFactory

```php
protected static ?\Psr\Http\Message\ResponseFactoryInterface $responseFactory
```

* This property is **static**.

***

### middlewareResolver

```php
protected static ?\Qubus\Routing\Interfaces\MiddlewareResolver $middlewareResolver
```

* This property is **static**.

***

## Methods

### create

```php
public static create(\Qubus\Routing\Interfaces\Collector $routeCollector, \Psr\Container\ContainerInterface $container, ?\Psr\Http\Message\ResponseFactoryInterface $responseFactory = null, ?\Qubus\Routing\Interfaces\MiddlewareResolver $middlewareResolver = null): \Qubus\Routing\Router
```

* This method is **static**.
**Parameters:**

| Parameter             | Type                                              | Description |
|-----------------------|---------------------------------------------------|-------------|
| `$routeCollector`     | **\Qubus\Routing\Interfaces\Collector**           |             |
| `$container`          | **\Psr\Container\ContainerInterface**             |             |
| `$responseFactory`    | **?\Psr\Http\Message\ResponseFactoryInterface**   |             |
| `$middlewareResolver` | **?\Qubus\Routing\Interfaces\MiddlewareResolver** |             |

***

### setRouteCollector

```php
public static setRouteCollector(\Qubus\Routing\Interfaces\Collector $routeCollector): void
```

* This method is **static**.
**Parameters:**

| Parameter         | Type                                    | Description |
|-------------------|-----------------------------------------|-------------|
| `$routeCollector` | **\Qubus\Routing\Interfaces\Collector** |             |

***

### setContainer

```php
public static setContainer(\Psr\Container\ContainerInterface $container): void
```

* This method is **static**.
**Parameters:**

| Parameter    | Type                                  | Description |
|--------------|---------------------------------------|-------------|
| `$container` | **\Psr\Container\ContainerInterface** |             |

***

### setResponseFactory

```php
public static setResponseFactory(\Psr\Http\Message\ResponseFactoryInterface $responseFactory): void
```

* This method is **static**.
**Parameters:**

| Parameter          | Type                                           | Description |
|--------------------|------------------------------------------------|-------------|
| `$responseFactory` | **\Psr\Http\Message\ResponseFactoryInterface** |             |

***

### setMiddlewareResolver

```php
public static setMiddlewareResolver(\Qubus\Routing\Interfaces\MiddlewareResolver $middlewareResolver): void
```

* This method is **static**.
**Parameters:**

| Parameter             | Type                                             | Description |
|-----------------------|--------------------------------------------------|-------------|
| `$middlewareResolver` | **\Qubus\Routing\Interfaces\MiddlewareResolver** |             |

***
