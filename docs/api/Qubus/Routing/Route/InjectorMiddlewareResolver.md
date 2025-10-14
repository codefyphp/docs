***

# InjectorMiddlewareResolver





* Full name: `\Qubus\Routing\Route\InjectorMiddlewareResolver`
* This class implements:
[`\Qubus\Routing\Interfaces\MiddlewareResolver`](../Interfaces/MiddlewareResolver.md)



## Properties


### container



```php
public \Psr\Container\ContainerInterface $container
```






***

## Methods


### __construct



```php
public __construct(\Psr\Container\ContainerInterface $container): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$container` | **\Psr\Container\ContainerInterface** |  |





***

### resolve

Resolves a middleware

```php
public resolve(mixed $name): \Psr\Http\Server\MiddlewareInterface|callable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** | The key to look up a middleware |





***


***
> Automatically generated on 2025-10-13
