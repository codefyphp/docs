# QueryHandlerResolver

***

* Full name: `\Codefy\QueryBus\QueryHandlerResolver`

## Methods

### resolve

Retrieve a $queryHandler for a given Query.

```php
public resolve(\Codefy\QueryBus\Query $query): \Codefy\QueryBus\QueryHandler
```

**Parameters:**

| Parameter | Type                       | Description |
|-----------|----------------------------|-------------|
| `$query`  | **\Codefy\QueryBus\Query** |             |

***

### bindHandler

Bind a handler to a query. These bindings should overrule the default
resolution behavior for this resolver.

```php
public bindHandler(string $queryName, \Codefy\QueryBus\QueryHandler|callable|string $handler): void
```

**Parameters:**

| Parameter    | Type                                                | Description |
|--------------|-----------------------------------------------------|-------------|
| `$queryName` | **string**                                          |             |
| `$handler`   | **\Codefy\QueryBus\QueryHandler\|callable\|string** |             |

***
