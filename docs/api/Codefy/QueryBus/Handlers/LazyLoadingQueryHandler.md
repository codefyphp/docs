# LazyLoadingQueryHandler

***

* Full name: `\Codefy\QueryBus\Handlers\LazyLoadingQueryHandler`
* This class implements:
  [`\Codefy\QueryBus\QueryHandler`](../QueryHandler.md)

## Properties

### handlerName

```php
public string $handlerName
```

***

### container

```php
public \Codefy\CommandBus\Container $container
```

***

## Methods

### __construct

```php
public __construct(string $handlerName, \Codefy\CommandBus\Container $container): mixed
```

**Parameters:**

| Parameter      | Type                             | Description |
|----------------|----------------------------------|-------------|
| `$handlerName` | **string**                       |             |
| `$container`   | **\Codefy\CommandBus\Container** |             |

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
