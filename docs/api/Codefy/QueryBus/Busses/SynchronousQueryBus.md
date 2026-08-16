# SynchronousQueryBus

***

* Full name: `\Codefy\QueryBus\Busses\SynchronousQueryBus`
* This class implements:
  [`\Codefy\QueryBus\QueryBus`](../QueryBus.md)

## Properties

### resolver

```php
protected \Codefy\QueryBus\QueryHandlerResolver $resolver
```

***

## Methods

### __construct

```php
public __construct(\Codefy\QueryBus\QueryHandlerResolver $resolver = new \Codefy\QueryBus\Resolvers\NativeQueryHandlerResolver()): mixed
```

**Parameters:**

| Parameter   | Type                                      | Description |
|-------------|-------------------------------------------|-------------|
| `$resolver` | **\Codefy\QueryBus\QueryHandlerResolver** |             |

***

### execute

Execute a command.

```php
public execute(\Codefy\QueryBus\Query $query): mixed
```

**Parameters:**

| Parameter | Type                       | Description |
|-----------|----------------------------|-------------|
| `$query`  | **\Codefy\QueryBus\Query** |             |

**Throws:**

- [`UnresolvableQueryHandlerException`](../UnresolvableQueryHandlerException.md)
- [`ReflectionException`](../../../ReflectionException.md)

***
