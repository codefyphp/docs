# Router

***

* Full name: `\Qubus\Routing\Router`
* This class implements:
  [`\Qubus\Routing\Psr7Router`](./Psr7Router.md),
  [`\Qubus\Routing\Interfaces\Mappable`](./Interfaces/Mappable.md),
  `MiddlewareInterface`

## Properties

### request

```php
public \Qubus\Http\Request $request
```

***

### version

```php
public string $version
```

***

### routes

```php
public array $routes
```

***

### routeCollector

```php
protected \Qubus\Routing\Interfaces\Collector $routeCollector
```

***

### routesCreated

```php
protected bool $routesCreated
```

***

### routeCollectorMatchTypeId

```php
protected int $routeCollectorMatchTypeId
```

***

### basePath

```php
protected string $basePath
```

***

### currentRoute

```php
protected ?\Qubus\Routing\Route\Route $currentRoute
```

***

### container

```php
protected ?\Psr\Container\ContainerInterface $container
```

***

### responseFactory

```php
protected ?\Psr\Http\Message\ResponseFactoryInterface $responseFactory
```

***

### middlewareResolver

```php
protected ?\Qubus\Routing\Interfaces\MiddlewareResolver $middlewareResolver
```

***

### invoker

```php
protected ?\Qubus\Routing\Invoker $invoker
```

***

### routeCache

```php
protected ?\Qubus\Routing\Route\RouteFileCache $routeCache
```

***

### baseMiddleware

```php
public array $baseMiddleware
```

***

### defaultNamespace

```php
protected ?string $defaultNamespace
```

***

### namespace

```php
protected string $namespace
```

***

### bootManagers

```php
protected array $bootManagers
```

***

### eventHandlers

```php
protected array $eventHandlers
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Routing\Interfaces\Collector $routeCollector, \Psr\Container\ContainerInterface $container, ?\Psr\Http\Message\ResponseFactoryInterface $responseFactory = null, ?\Qubus\Routing\Interfaces\MiddlewareResolver $resolver = null): mixed
```

**Parameters:**

| Parameter          | Type                                              | Description |
|--------------------|---------------------------------------------------|-------------|
| `$routeCollector`  | **\Qubus\Routing\Interfaces\Collector**           |             |
| `$container`       | **\Psr\Container\ContainerInterface**             |             |
| `$responseFactory` | **?\Psr\Http\Message\ResponseFactoryInterface**   |             |
| `$resolver`        | **?\Qubus\Routing\Interfaces\MiddlewareResolver** |             |

***

### prependUrl

```php
public prependUrl(string $url): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$url`    | **string** |             |

***

### setContainer

Set a container.

```php
protected setContainer(\Psr\Container\ContainerInterface $container): void
```

**Parameters:**

| Parameter    | Type                                  | Description |
|--------------|---------------------------------------|-------------|
| `$container` | **\Psr\Container\ContainerInterface** |             |

***

### setBasePath

Set the basepath.

```php
public setBasePath(string $basePath): void
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$basePath` | **string** |             |

***

### setDefaultNamespace

Set the default namespace for controllers.

```php
public setDefaultNamespace(string $namespace): void
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$namespace` | **string** |             |

***

### enableRouteCache

Use this method to enable route caching.

```php
public enableRouteCache(string $file): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$file`   | **string** |             |

***

### disableRouteCache

Disable route caching for this router instance.

```php
public disableRouteCache(): void
```

***

### hasRouteCache

```php
public hasRouteCache(): bool
```

***

### addRoute

Add route.

```php
protected addRoute(\Qubus\Routing\Route\Route $route): void
```

**Parameters:**

| Parameter | Type                           | Description |
|-----------|--------------------------------|-------------|
| `$route`  | **\Qubus\Routing\Route\Route** | The route.  |

**Return Value:**

Add route to routes array.

**Throws:**

- [`TooLateToAddNewRouteException`](./Exceptions/TooLateToAddNewRouteException.md)

***

### convertRouteToRouteCollectorRouterUri

```php
protected convertRouteToRouteCollectorRouterUri(\Qubus\Routing\Interfaces\Routable $route, \Qubus\Routing\Route\RouteCollector $routeCollector): string
```

**Parameters:**

| Parameter         | Type                                    | Description |
|-------------------|-----------------------------------------|-------------|
| `$route`          | **\Qubus\Routing\Interfaces\Routable**  |             |
| `$routeCollector` | **\Qubus\Routing\Route\RouteCollector** |             |

***

### map

Add a route to the map

```php
public map(array $verbs, string $uri, callable|string $callback): \Qubus\Routing\Route\Route
```

**Parameters:**

| Parameter   | Type                 | Description   |
|-------------|----------------------|---------------|
| `$verbs`    | **array**            | HTTP methods. |
| `$uri`      | **string**           | Route path.   |
| `$callback` | **callable\|string** |               |

**Throws:**

- [`TooLateToAddNewRouteException`](./Exceptions/TooLateToAddNewRouteException.md)

***

### resources

Register an array of resource controllers.

```php
public resources(array $resources, array $options = []): void
```

**Parameters:**

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `$resources` | **array** |             |
| `$options`   | **array** |             |

***

### resource

Route a resource to a controller.

```php
public resource(string $name, string $controller, array $options = []): mixed
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$name`       | **string** |             |
| `$controller` | **string** |             |
| `$options`    | **array**  |             |

***

### apiResources

Register an array of API resource controllers.

```php
public apiResources(array $resources, array $options = []): void
```

**Parameters:**

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `$resources` | **array** |             |
| `$options`   | **array** |             |

***

### apiResource

Route an API resource to a controller.

```php
public apiResource(string $name, string $controller, array $options = []): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$name`       | **string** |             |
| `$controller` | **string** |             |
| `$options`    | **array**  |             |

***

### loadRoutesFromJson

Load routes from a JSON file.

```php
public loadRoutesFromJson(string $path): void
```

**Parameters:**

| Parameter | Type       | Description                   |
|-----------|------------|-------------------------------|
| `$path`   | **string** | Path to the JSON routes file. |

**Throws:**

- [`\Qubus\Routing\Exceptions\TooLateToAddNewRouteException|\Qubus\Exception\Data\TypeException`](./Exceptions/TooLateToAddNewRouteException|/Qubus/Exception/Data/TypeException.md)

***

### handleSimpleJsonRoutes

Converts JSON routes to a route object.

```php
public handleSimpleJsonRoutes(array $route): void
```

**Parameters:**

| Parameter | Type      | Description           |
|-----------|-----------|-----------------------|
| `$route`  | **array** | Array from JSON file. |

**Throws:**

- [`\Qubus\Routing\Exceptions\TooLateToAddNewRouteException|\Qubus\Exception\Data\TypeException`](./Exceptions/TooLateToAddNewRouteException|/Qubus/Exception/Data/TypeException.md)

***

### handleGroupJsonRoutes

Converts JSON group routes to a route object.

```php
public handleGroupJsonRoutes(array $route): void
```

**Parameters:**

| Parameter | Type      | Description           |
|-----------|-----------|-----------------------|
| `$route`  | **array** | Array form JSON file. |

**Throws:**

- [`\Qubus\Routing\Exceptions\TooLateToAddNewRouteException|\Qubus\Exception\Data\TypeException`](./Exceptions/TooLateToAddNewRouteException|/Qubus/Exception/Data/TypeException.md)

***

### buildRoutes

```php
protected buildRoutes(): void
```

***

### createRoutes

```php
protected createRoutes(): void
```

***

### exportCompiledRoutes

```php
protected exportCompiledRoutes(): array
```

***

### importCompiledRoutes

```php
protected importCompiledRoutes(array $compiled): void
```

**Parameters:**

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `$compiled` | **array** |             |

***

### normalizeHttpMethod

Method to override/normalize the HTTP method before match/dispatch.

```php
protected normalizeHttpMethod(\Psr\Http\Message\ServerRequestInterface $request): \Psr\Http\Message\ServerRequestInterface
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

***

### hydrateRoute

Add route.

```php
public hydrateRoute(\Qubus\Routing\Route\Route $route): void
```

**Parameters:**

| Parameter | Type                           | Description |
|-----------|--------------------------------|-------------|
| `$route`  | **\Qubus\Routing\Route\Route** | The route.  |

**Return Value:**

Add route to routes array.

**Throws:**

- [`TooLateToAddNewRouteException`](./Exceptions/TooLateToAddNewRouteException.md)

***

### match

Match a given Request Url against stored routes
converted into a Response.

```php
public match(\Psr\Http\Message\ServerRequestInterface $serverRequest): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter        | Type                                         | Description |
|------------------|----------------------------------------------|-------------|
| `$serverRequest` | **\Psr\Http\Message\ServerRequestInterface** |             |

**Throws:**

- [`Exception`](../../Exception.md)

***

### handle

```php
protected handle(object $route, \Psr\Http\Message\ServerRequestInterface $serverRequest, \Qubus\Routing\Route\RouteParams $params): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter        | Type                                         | Description |
|------------------|----------------------------------------------|-------------|
| `$route`         | **object**                                   |             |
| `$serverRequest` | **\Psr\Http\Message\ServerRequestInterface** |             |
| `$params`        | **\Qubus\Routing\Route\RouteParams**         |             |

***

### addBootManager

Add BootManager

```php
public addBootManager(\Qubus\Routing\Interfaces\BootManager $bootManager): static
```

**Parameters:**

| Parameter      | Type                                      | Description |
|----------------|-------------------------------------------|-------------|
| `$bootManager` | **\Qubus\Routing\Interfaces\BootManager** |             |

***

### has

Check if a route exists based on its name.

```php
public has(string $name): bool
```

**Parameters:**

| Parameter | Type       | Description            |
|-----------|------------|------------------------|
| `$name`   | **string** | The name of the route. |

**Return Value:**

True if the named routed exists, false otherwise.

***

### url

Generate url's from named routes.

```php
public url(string $name, array $params = []): string
```

**Parameters:**

| Parameter | Type       | Description        |
|-----------|------------|--------------------|
| `$name`   | **string** | Name of the route. |
| `$params` | **array**  | Data parameters.   |

**Return Value:**

The url.

***

### redirect

Redirect one route to another.

```php
public redirect(string $from, string $to, int $status = 302): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter | Type       | Description        |
|-----------|------------|--------------------|
| `$from`   | **string** | Originating route. |
| `$to`     | **string** | Destination route. |
| `$status` | **int**    | HTTP status code.  |

***

### permanentRedirect

Create a permanent redirect from one URI to another.

```php
public permanentRedirect(string $uri, string $destination): \Qubus\Routing\Interfaces\Routable|\Qubus\Routing\Interfaces\Mappable
```

**Parameters:**

| Parameter      | Type       | Description |
|----------------|------------|-------------|
| `$uri`         | **string** |             |
| `$destination` | **string** |             |

**Throws:**

- [`TooLateToAddNewRouteException`](./Exceptions/TooLateToAddNewRouteException.md)

***

### group

Add route group

```php
public group(array|string $params, callable $callback): self
```

**Parameters:**

| Parameter   | Type              | Description |
|-------------|-------------------|-------------|
| `$params`   | **array\|string** |             |
| `$callback` | **callable**      |             |

***

### getBasePath

Get the basepath.

```php
public getBasePath(): string
```

**Return Value:**

The basepath.

***

### currentRoute

Get current route.

```php
public currentRoute(): \Qubus\Routing\Route\Route|null
```

**Return Value:**

Current route.

***

### currentRouteName

Get current route name.

```php
public currentRouteName(): null|string
```

**Return Value:**

Current route name.

***

### setEventHandlers

Register event handler

```php
public setEventHandlers(\Qubus\Routing\Events\EventHandler $handler): void
```

**Parameters:**

| Parameter  | Type                                   | Description |
|------------|----------------------------------------|-------------|
| `$handler` | **\Qubus\Routing\Events\EventHandler** |             |

***

### getEventHandlers

Get registered event-handler.

```php
public getEventHandlers(): array
```

***

### fireEvents

Fire event in event-handler.

```php
protected fireEvents(string $name, array $arguments = []): void
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$name`      | **string** |             |
| `$arguments` | **array**  |             |

***

### setExtrasOfSimpleJsonRoute

Sets other router methods.

```php
private setExtrasOfSimpleJsonRoute(array $extras, \Qubus\Routing\Interfaces\Routable $route): void
```

**Parameters:**

| Parameter | Type                                   | Description        |
|-----------|----------------------------------------|--------------------|
| `$extras` | **array**                              | Router attributes. |
| `$route`  | **\Qubus\Routing\Interfaces\Routable** | Route object.      |

**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)

***

### process

```php
public process(\Psr\Http\Message\ServerRequestInterface $request, \Psr\Http\Server\RequestHandlerInterface $handler): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |
| `$handler` | **\Psr\Http\Server\RequestHandlerInterface** |             |

**Throws:**

- [`Exception`](../../Exception.md)

***

## Inherited methods

### map

Add a route to the map.

```php
public map(array $verbs, string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

* This method is **abstract**.
**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$verbs`    | **array**            |             |
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

***

### any

Add a route that responds to any HTTP method.

```php
public any(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

**Throws:**

- [`TooLateToAddNewRouteException`](./Exceptions/TooLateToAddNewRouteException.md)

***

### get

Add a route that responds to GET HTTP method.

```php
public get(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

**Throws:**

- [`TooLateToAddNewRouteException`](./Exceptions/TooLateToAddNewRouteException.md)

***

### post

Add a route that responds to POST HTTP method.

```php
public post(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

**Throws:**

- [`TooLateToAddNewRouteException`](./Exceptions/TooLateToAddNewRouteException.md)

***

### patch

Add a route that responds to PATCH HTTP method.

```php
public patch(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

**Throws:**

- [`TooLateToAddNewRouteException`](./Exceptions/TooLateToAddNewRouteException.md)

***

### put

Add a route that responds to PUT HTTP method.

```php
public put(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

**Throws:**

- [`TooLateToAddNewRouteException`](./Exceptions/TooLateToAddNewRouteException.md)

***

### delete

Add a route that responds to DELETE HTTP method.

```php
public delete(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

**Throws:**

- [`TooLateToAddNewRouteException`](./Exceptions/TooLateToAddNewRouteException.md)

***

### head

Add a route that responds to HEAD HTTP method.

```php
public head(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

**Throws:**

- [`TooLateToAddNewRouteException`](./Exceptions/TooLateToAddNewRouteException.md)

***

### options

Add a route that responds to OPTIONS HTTP method.

```php
public options(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

**Throws:**

- [`TooLateToAddNewRouteException`](./Exceptions/TooLateToAddNewRouteException.md)

***

### connect

Add a route that responds to CONNECT HTTP method.

```php
public connect(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

**Throws:**

- [`TooLateToAddNewRouteException`](./Exceptions/TooLateToAddNewRouteException.md)

***

### trace

Add a route that responds to TRACE HTTP method.

```php
public trace(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

**Throws:**

- [`TooLateToAddNewRouteException`](./Exceptions/TooLateToAddNewRouteException.md)

***
