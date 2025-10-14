***

# RoutingRegistrar





* Full name: `\Qubus\Routing\Route\RoutingRegistrar`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### router



```php
private \Qubus\Routing\Router $router
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Routing\Router $router): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$router` | **\Qubus\Routing\Router** |  |





***

### load



```php
public load(array|string|callable $sources): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$sources` | **array&#124;string&#124;callable** |  |




**Throws:**

- [`JsonException`](../../../JsonException.md)

- [`TooLateToAddNewRouteException`](../Exceptions/TooLateToAddNewRouteException.md)

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### group



```php
public group(array|string|callable $sources, array $middleware = [], string $prefix = &#039;&#039;): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$sources` | **array&#124;string&#124;callable** |  |
| `$middleware` | **array** |  |
| `$prefix` | **string** |  |





***

### loadOne



```php
private loadOne(string|callable $source): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$source` | **string&#124;callable** |  |




**Throws:**

- [`TooLateToAddNewRouteException`](../Exceptions/TooLateToAddNewRouteException.md)

- [`JsonException`](../../../JsonException.md)

- [`TypeException`](../../Exception/Data/TypeException.md)



***


***
> Automatically generated on 2025-10-13
