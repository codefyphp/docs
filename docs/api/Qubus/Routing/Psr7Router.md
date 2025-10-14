***

# Psr7Router





* Full name: `\Qubus\Routing\Psr7Router`



## Methods


### match

Match a given Request Url against stored routes
converted into a Response.

```php
public match(\Psr\Http\Message\ServerRequestInterface $serverRequest): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$serverRequest` | **\Psr\Http\Message\ServerRequestInterface** |  |





***

### has

Check if a route exists based on its name.

```php
public has(string $name): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | The name of the route. |


**Return Value:**

True if the named routed exists, false otherwise.




***

### url

Generate url's from named routes.

```php
public url(string $name, array $params = []): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | Name of the route. |
| `$params` | **array** | Data parameters. |


**Return Value:**

The url.



**Throws:**

- [`RouteParamFailedConstraintException`](./Exceptions/RouteParamFailedConstraintException.md)

- [`NamedRouteNotFoundException`](./Exceptions/NamedRouteNotFoundException.md)



***

### redirect

Redirect one route to another.

```php
public redirect(string $from, string $to, int $status = 302): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$from` | **string** | Originating route. |
| `$to` | **string** | Destination route. |
| `$status` | **int** | HTTP status code. |




**Throws:**

- [`TooLateToAddNewRouteException`](./Exceptions/TooLateToAddNewRouteException.md)



***


***
> Automatically generated on 2025-10-13
