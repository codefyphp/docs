***

# PresenceVerifier





* Full name: `\Qubus\Validation\Interfaces\PresenceVerifier`



## Methods


### getCount

Count the number of objects in a collection having the given value.

```php
public getCount(string $collection, string $column, string $value, int|null $excludeId = null, string|null $idColumn = null, array $extra = []): int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$collection` | **string** |  |
| `$column` | **string** |  |
| `$value` | **string** |  |
| `$excludeId` | **int&#124;null** |  |
| `$idColumn` | **string&#124;null** |  |
| `$extra` | **array** |  |





***

### getMultiCount

Count the number of objects in a collection with the given values.

```php
public getMultiCount(string $collection, string $column, array $values, array $extra = []): int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$collection` | **string** |  |
| `$column` | **string** |  |
| `$values` | **array** |  |
| `$extra` | **array** |  |





***


***
> Automatically generated on 2025-10-13
