***

# RouteFactory





* Full name: `\Qubus\Routing\Factories\RouteFactory`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Qubus\Routing\Factories\RoutableFactory`](./RoutableFactory.md)
* This class is a **Final class**



## Properties


### invoker



```php
protected static ?\Invoker\InvokerInterface $invoker
```



* This property is **static**.


***

### middlewareResolver



```php
protected static ?\Qubus\Routing\Interfaces\MiddlewareResolver $middlewareResolver
```



* This property is **static**.


***

## Methods


### create



```php
public static create(array $methods, string $uri, mixed $action, ?string $defaultNamespace = null, ?\Invoker\InvokerInterface $invoker = null, ?\Qubus\Routing\Interfaces\MiddlewareResolver $middlewareResolver = null): \Qubus\Routing\Route\Route
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$methods` | **array** |  |
| `$uri` | **string** |  |
| `$action` | **mixed** |  |
| `$defaultNamespace` | **?string** |  |
| `$invoker` | **?\Invoker\InvokerInterface** |  |
| `$middlewareResolver` | **?\Qubus\Routing\Interfaces\MiddlewareResolver** |  |





***

### setInvoker



```php
public static setInvoker(\Invoker\InvokerInterface $invoker): void
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$invoker` | **\Invoker\InvokerInterface** |  |





***

### setMiddlewareResolver



```php
public static setMiddlewareResolver(\Qubus\Routing\Interfaces\MiddlewareResolver $middlewareResolver): void
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$middlewareResolver` | **\Qubus\Routing\Interfaces\MiddlewareResolver** |  |





***


***
> Automatically generated on 2025-10-13
