# Mappable

***

* Full name: `\Qubus\Routing\Interfaces\Mappable`

## Constants


| Constant              | Visibility | Type | Value     |
|-----------------------|------------|------|-----------|
| `HTTP_METHOD_GET`     | public     |      | 'GET'     |
| `HTTP_METHOD_POST`    | public     |      | 'POST'    |
| `HTTP_METHOD_PUT`     | public     |      | 'PUT'     |
| `HTTP_METHOD_PATCH`   | public     |      | 'PATCH'   |
| `HTTP_METHOD_OPTIONS` | public     |      | 'OPTIONS' |
| `HTTP_METHOD_DELETE`  | public     |      | 'DELETE'  |
| `HTTP_METHOD_HEAD`    | public     |      | 'HEAD'    |
| `HTTP_METHOD_TRACE`   | public     |      | 'TRACE'   |
| `HTTP_METHOD_CONNECT` | public     |      | 'CONNECT' |

## Methods

### map

Add a route to the map

```php
public map(array $verbs, string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

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

***

### get

Add a route that responds to GET HTTP method

```php
public get(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

***

### post

Add a route that responds to POST HTTP method

```php
public post(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

***

### patch

Add a route that responds to PATCH HTTP method

```php
public patch(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

***

### put

Add a route that responds to PUT HTTP method

```php
public put(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

***

### delete

Add a route that responds to DELETE HTTP method

```php
public delete(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

***

### head

Add a route that responds to HEAD HTTP method

```php
public head(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

***

### options

Add a route that responds to OPTIONS HTTP method

```php
public options(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter   | Type                 | Description |
|-------------|----------------------|-------------|
| `$uri`      | **string**           |             |
| `$callback` | **callable\|string** |             |

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
