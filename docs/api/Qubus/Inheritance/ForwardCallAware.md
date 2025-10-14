***

# ForwardCallAware





* Full name: `\Qubus\Inheritance\ForwardCallAware`




## Methods


### forwardCallTo

Forward a method call to the given object.

```php
protected forwardCallTo(mixed $object, string $method, array $parameters = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$object` | **mixed** |  |
| `$method` | **string** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`BadMethodCallException`](../../BadMethodCallException.md)



***

### forwardDecoratedCallTo

Forward a method call to the given object, returning $this if the forwarded call returned itself.

```php
protected forwardDecoratedCallTo(mixed $object, string $method, array $parameters = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$object` | **mixed** |  |
| `$method` | **string** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`BadMethodCallException`](../../BadMethodCallException.md)



***

### throwBadMethodCallException

Throw a bad method call exception for the given method.

```php
protected static throwBadMethodCallException(string $method): never
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$method` | **string** |  |




**Throws:**

- [`BadMethodCallException`](../../BadMethodCallException.md)



***

***
> Automatically generated on 2025-10-13

