# Enquire

***

* Full name: `\Codefy\QueryBus\Enquire`
* This class implements:
  [`\Codefy\QueryBus\QueryBus`](./QueryBus.md)

## Properties

### bus

```php
protected \Codefy\QueryBus\QueryBus $bus
```

***

## Methods

### __construct

Constructor.

```php
public __construct(\Codefy\QueryBus\QueryBus $bus = new \Codefy\QueryBus\Busses\SynchronousQueryBus()): mixed
```

**Parameters:**

| Parameter | Type                          | Description |
|-----------|-------------------------------|-------------|
| `$bus`    | **\Codefy\QueryBus\QueryBus** |             |

***

### execute

Execute a query.

```php
public execute(\Codefy\QueryBus\Query $query): mixed
```

**Parameters:**

| Parameter | Type                       | Description |
|-----------|----------------------------|-------------|
| `$query`  | **\Codefy\QueryBus\Query** |             |

**Throws:**

- [`UnresolvableQueryHandlerException`](./UnresolvableQueryHandlerException.md)
- [`ReflectionException`](../../ReflectionException.md)

***
