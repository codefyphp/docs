# CallableQueryHandler

***

* Full name: `\Codefy\QueryBus\Handlers\CallableQueryHandler`
* This class implements:
  [`\Codefy\QueryBus\QueryHandler`](../QueryHandler.md)

## Properties

### handler

```php
protected callable $handler
```

***

## Methods

### __construct

```php
public __construct(callable $handler): mixed
```

**Parameters:**

| Parameter  | Type         | Description |
|------------|--------------|-------------|
| `$handler` | **callable** |             |

***

### handle

Handle a query execution.

```php
public handle(\Codefy\QueryBus\Query $query): mixed
```

**Parameters:**

| Parameter | Type                       | Description |
|-----------|----------------------------|-------------|
| `$query`  | **\Codefy\QueryBus\Query** |             |

***
