# NativeQueryHandlerResolver

***

* Full name: `\Codefy\QueryBus\Resolvers\NativeQueryHandlerResolver`
* This class implements:
  [`\Codefy\QueryBus\QueryHandlerResolver`](../QueryHandlerResolver.md)

## Properties

### handlers

```php
protected \Codefy\QueryBus\QueryHandler[] $handlers
```

***

### container

```php
protected \Codefy\CommandBus\Container $container
```

***

## Methods

### __construct

```php
public __construct(\Codefy\CommandBus\Container $container = new \Codefy\CommandBus\Containers\NativeContainer()): mixed
```

**Parameters:**

| Parameter    | Type                             | Description |
|--------------|----------------------------------|-------------|
| `$container` | **\Codefy\CommandBus\Container** |             |

***

### resolve

Retrieve a QueryHandler for a given Command

```php
public resolve(\Codefy\QueryBus\Query $query): \Codefy\QueryBus\QueryHandler
```

**Parameters:**

| Parameter | Type                       | Description |
|-----------|----------------------------|-------------|
| `$query`  | **\Codefy\QueryBus\Query** |             |

**Throws:**

- [`UnresolvableQueryHandlerException`](../UnresolvableQueryHandlerException.md)
- [`ReflectionException`](../../../ReflectionException.md)

***

### bindHandler

Bind a handler to a query. These bindings should overrule the default
resolution behavior for this resolver.

```php
public bindHandler(string $queryName, callable|string|\Codefy\QueryBus\QueryHandler $handler): void
```

**Parameters:**

| Parameter    | Type                                                | Description |
|--------------|-----------------------------------------------------|-------------|
| `$queryName` | **string**                                          |             |
| `$handler`   | **callable\|string\|\Codefy\QueryBus\QueryHandler** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***
