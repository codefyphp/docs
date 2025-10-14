***

# Identifier





* Full name: `\Qubus\Expressive\Identifier`
* Parent class: [`\Qubus\Expressive\Expression`](./Expression.md)




## Methods


### handle

Handles identifier quoting.

```php
public handle(mixed $connection): \Qubus\Expressive\Connection
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$connection` | **mixed** |  |


**Return Value:**

$connection quoted identifier




***


## Inherited methods


### __construct



```php
public __construct(mixed $value): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **mixed** | expression value |





***

### value

Get the expression value as a string.

```php
public value(): string
```

$sql = $expression->value();










***

### __toString

Return the value of the expression as a string.

```php
public __toString(): string
```

echo $expression;










***


***
> Automatically generated on 2025-10-13
