# Collector

***

* Full name: `\Qubus\Routing\Interfaces\Collector`

## Methods

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

### map

Map a route to a target

```php
public map(string $method, string $domain, string $route, mixed $target, null|string $name = null): void
```

**Parameters:**

| Parameter | Type             | Description                                                                                                 |
|-----------|------------------|-------------------------------------------------------------------------------------------------------------|
| `$method` | **string**       | One of 5 HTTP Methods, or a pipe-separated list
of multiple HTTP Methods (GET\|POST\|PATCH\|PUT\|DELETE)    |
| `$domain` | **string**       |                                                                                                             |
| `$route`  | **string**       | The route regex, custom regex must start with an @.
You can use multiple pre-set regex filters, like [i:id] |
| `$target` | **mixed**        | The target where this route should point to. Can be anything.                                               |
| `$name`   | **null\|string** | Optional name of this route. Supply if you want to
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

- [`RuntimeException`](../../../RuntimeException.md)

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
