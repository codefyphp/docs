# RouterableFactory

***

* Full name: `\Qubus\Routing\Factories\RouterableFactory`

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
