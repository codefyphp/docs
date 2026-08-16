# RoutingEventArgument

***

* Full name: `\Qubus\Routing\Events\RoutingEventArgument`
* This class implements:
  [`\Qubus\Routing\Events\EventArgument`](./EventArgument.md)

## Properties

### eventName

Event name

```php
public string $eventName
```

***

### router

```php
public \Qubus\Routing\Router $router
```

***

### arguments

```php
public array $arguments
```

***

## Methods

### __construct

```php
public __construct(string $eventName, \Qubus\Routing\Router $router, array $arguments = []): mixed
```

**Parameters:**

| Parameter    | Type                      | Description |
|--------------|---------------------------|-------------|
| `$eventName` | **string**                |             |
| `$router`    | **\Qubus\Routing\Router** |             |
| `$arguments` | **array**                 |             |

***

### getRequest

Get the request instance.

```php
public getRequest(): \Qubus\Http\Request|\Psr\Http\Message\RequestInterface
```

***

### __get

```php
public __get(string $name): mixed
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### __isset

```php
public __isset(string $name): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### __set

```php
public __set(string $name, mixed $value): mixed
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |
| `$value`  | **mixed**  |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***
