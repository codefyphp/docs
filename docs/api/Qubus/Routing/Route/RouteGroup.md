***

# RouteGroup





* Full name: `\Qubus\Routing\Route\RouteGroup`
* This class implements:
[`\Qubus\Routing\Interfaces\Mappable`](../Interfaces/Mappable.md)



## Properties


### router



```php
protected ?\Qubus\Routing\Router $router
```






***

### prefix



```php
protected string $prefix
```






***

### domain



```php
protected string $domain
```






***

### subDomain



```php
protected string $subDomain
```






***

### namespace



```php
protected string $namespace
```






***

### middlewares



```php
protected array $middlewares
```






***

## Methods


### __construct



```php
public __construct(string|array $params, \Qubus\Routing\Router $router): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$params` | **string&#124;array** |  |
| `$router` | **\Qubus\Routing\Router** |  |





***

### appendPrefixToUri



```php
private appendPrefixToUri(string $uri): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |





***

### map

Add a route to the map

```php
public map(array $verbs, string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$verbs` | **array** |  |
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |




**Throws:**

- [`TooLateToAddNewRouteException`](../Exceptions/TooLateToAddNewRouteException.md)



***

### group

Add route group

```php
public group(array|string $params, callable $callback): \Qubus\Routing\Route\RouteGroup
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$params` | **array&#124;string** |  |
| `$callback` | **callable** |  |





***


## Inherited methods


### map

Add a route to the map.

```php
public map(array $verbs, string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```




* This method is **abstract**.



**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$verbs` | **array** |  |
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |





***

### any

Add a route that responds to any HTTP method.

```php
public any(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |




**Throws:**

- [`TooLateToAddNewRouteException`](../Exceptions/TooLateToAddNewRouteException.md)



***

### get

Add a route that responds to GET HTTP method.

```php
public get(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |




**Throws:**

- [`TooLateToAddNewRouteException`](../Exceptions/TooLateToAddNewRouteException.md)



***

### post

Add a route that responds to POST HTTP method.

```php
public post(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |




**Throws:**

- [`TooLateToAddNewRouteException`](../Exceptions/TooLateToAddNewRouteException.md)



***

### patch

Add a route that responds to PATCH HTTP method.

```php
public patch(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |




**Throws:**

- [`TooLateToAddNewRouteException`](../Exceptions/TooLateToAddNewRouteException.md)



***

### put

Add a route that responds to PUT HTTP method.

```php
public put(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |




**Throws:**

- [`TooLateToAddNewRouteException`](../Exceptions/TooLateToAddNewRouteException.md)



***

### delete

Add a route that responds to DELETE HTTP method.

```php
public delete(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |




**Throws:**

- [`TooLateToAddNewRouteException`](../Exceptions/TooLateToAddNewRouteException.md)



***

### head

Add a route that responds to HEAD HTTP method.

```php
public head(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |




**Throws:**

- [`TooLateToAddNewRouteException`](../Exceptions/TooLateToAddNewRouteException.md)



***

### options

Add a route that responds to OPTIONS HTTP method.

```php
public options(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |




**Throws:**

- [`TooLateToAddNewRouteException`](../Exceptions/TooLateToAddNewRouteException.md)



***

### connect

Add a route that responds to CONNECT HTTP method.

```php
public connect(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |




**Throws:**

- [`TooLateToAddNewRouteException`](../Exceptions/TooLateToAddNewRouteException.md)



***

### trace

Add a route that responds to TRACE HTTP method.

```php
public trace(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |




**Throws:**

- [`TooLateToAddNewRouteException`](../Exceptions/TooLateToAddNewRouteException.md)



***


***
> Automatically generated on 2025-10-13
