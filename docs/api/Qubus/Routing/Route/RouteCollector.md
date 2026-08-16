# RouteCollector

***

* Full name: `\Qubus\Routing\Route\RouteCollector`
* This class implements:
  [`\Qubus\Routing\Interfaces\Collector`](../Interfaces/Collector.md)

## Properties

### routes

```php
public array $routes
```

***

### namedRoutes

```php
protected array $namedRoutes
```

***

### domain

```php
public ?string $domain
```

***

### subdomain

```php
protected ?string $subdomain
```

***

### basePath

```php
public string $basePath
```

***

### matchTypes

```php
protected array $matchTypes
```

***

## Methods

### __construct

Create router.

```php
public __construct(array $routes = [], string $basePath = '', array $matchTypes = []): mixed
```

**Parameters:**

| Parameter     | Type       | Description       |
|---------------|------------|-------------------|
| `$routes`     | **array**  |                   |
| `$basePath`   | **string** | Set the basepath. |
| `$matchTypes` | **array**  | Set regexes.      |

**Throws:**

- [`RuntimeException`](../../../RuntimeException.md)

***

### addRoutes

Add multiple routes at once from array using the following format:

```php
public addRoutes(array $routes): void
```

$routes = [
   [$method, $route, $target, $name]
];

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$routes` | **array** |             |

**Throws:**

- [`RuntimeException`](../../../RuntimeException.md)

***

### addMatchTypes

Add named match types. It uses array_merge so keys can be overwritten.

```php
public addMatchTypes(array $matchTypes): void
```

**Parameters:**

| Parameter     | Type      | Description                                     |
|---------------|-----------|-------------------------------------------------|
| `$matchTypes` | **array** | The key is the name and the value is the regex. |

***

### map

Map a route to a target

```php
public map(string $method, ?string $subdomain, string $route, mixed $target, null|string $name = null): void
```

**Parameters:**

| Parameter    | Type             | Description                                                                                                 |
|--------------|------------------|-------------------------------------------------------------------------------------------------------------|
| `$method`    | **string**       | One of 5 HTTP Methods, or a pipe-separated list
of multiple HTTP Methods (GET\|POST\|PATCH\|PUT\|DELETE)    |
| `$subdomain` | **?string**      | Domain of route.                                                                                            |
| `$route`     | **string**       | The route regex, custom regex must start with an @.
You can use multiple pre-set regex filters, like [i:id] |
| `$target`    | **mixed**        | The target where this route should point to. Can be anything.                                               |
| `$name`      | **null\|string** | Optional name of this route. Supply if you want to
reverse route this url in your application.              |

**Throws:**

- [`RuntimeException`](../../../RuntimeException.md)

***

### generateUri

Reversed routing

```php
public generateUri(string $routeName, array $params = []): string
```

Generate the URL for a named route. Replace regexes with supplied parameters

**Parameters:**

| Parameter    | Type       | Description                                                   |
|--------------|------------|---------------------------------------------------------------|
| `$routeName` | **string** | The name of the route.                                        |
| `$params`    | **array**  | Associative array of parameters to replace placeholders with. |

**Return Value:**

The URL of the route with named parameters in place.

**Throws:**

- [`NamedRouteNotFoundException`](../Exceptions/NamedRouteNotFoundException.md)

***

### match

Match a given Request Url against stored routes

```php
public match(?string $requestHost = null, ?string $requestUrl = null, ?string $requestMethod = null): array|bool
```

**Parameters:**

| Parameter        | Type        | Description |
|------------------|-------------|-------------|
| `$requestHost`   | **?string** |             |
| `$requestUrl`    | **?string** |             |
| `$requestMethod` | **?string** |             |

**Return Value:**

Array with route information on success, false on failure (no match).

**Throws:**

- [`Exception`](../../Exception/Exception.md)

***

### prependUrl

Adds a path at the beginning of a url.

```php
public prependUrl(string $basePath): void
```

Useful if you are running your application from a subdirectory.

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$basePath` | **string** |             |

***

### compileRoute

Compile the regex for a given route.

```php
protected compileRoute(mixed $route): string
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$route`  | **mixed** |             |

***
