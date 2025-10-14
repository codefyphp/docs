***

# Enquire





* Full name: `\Codefy\QueryBus\Enquire`
* This class implements:
[`\Codefy\QueryBus\QueryBus`](./QueryBus.md)



## Properties


### bus



```php
protected ?\Codefy\QueryBus\QueryBus $bus
```






***

## Methods


### __construct

Constructor.

```php
public __construct(\Codefy\QueryBus\QueryBus|null $bus = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$bus` | **\Codefy\QueryBus\QueryBus&#124;null** |  |





***

### execute

Execute a query.

```php
public execute(\Codefy\QueryBus\Query $query): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$query` | **\Codefy\QueryBus\Query** |  |




**Throws:**

- [`ReflectionException`](../../ReflectionException.md)

- [`UnresolvableQueryHandlerException`](./UnresolvableQueryHandlerException.md)



***


***
> Automatically generated on 2025-10-13
