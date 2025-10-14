***

# Model





* Full name: `\Qubus\Expressive\ActiveRecord\Model`


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`DATE_FORMAT`|public| |&#039;Y-m-d H:i:s.u&#039;|

## Properties


### connection

Database connection.

```php
protected static ?\Qubus\Expressive\Connection $connection
```



* This property is **static**.


***

### queryBuilder

Default orm query builder.

```php
protected ?\Qubus\Expressive\QueryBuilder $queryBuilder
```






***

### tableName

Database table name.

```php
protected ?string $tableName
```






***

### tablePrefix

Database table prefix.

```php
protected ?string $tablePrefix
```






***

### foreignKey

Parent key found in related model.

```php
protected string $foreignKey
```






***

### primaryKey

Primary key of parent model.

```php
protected string $primaryKey
```






***

### incrementing



```php
protected bool $incrementing
```






***

### exists



```php
public bool $exists
```






***

### data

Query result data.

```php
protected array $data
```






***

### relations

To stored loaded relation.

```php
protected array $relations
```






***

### fillable

Whitelist of attributes that are checked for mass assignment.

```php
protected array $fillable
```






***

### guarded

Blacklist of attributes that cannot be mass-assigned.

```php
protected array $guarded
```






***

### guardFlag

Flag of whether fillable/guarded attributes should be guarded.

```php
protected bool $guardFlag
```






***

### isReadOnly

Sets whether model is read only.

```php
protected bool $isReadOnly
```






***

## Methods


### __construct



```php
public __construct(array $newData = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$newData` | **array** |  |





***

### connection



```php
public static connection(\Qubus\Expressive\Connection $connection): \Qubus\Expressive\Connection
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$connection` | **\Qubus\Expressive\Connection** |  |





***

### dbalQuery



```php
protected dbalQuery(): \Qubus\Expressive\QueryBuilder
```












***

### query



```php
protected query(): static
```












***

### all



```php
protected all(string|array $columns = &#039;*&#039;): \Qubus\Expressive\ActiveRecord\Result
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columns` | **string&#124;array** |  |





***

### get



```php
protected get(string|array $columns = &#039;*&#039;): \Qubus\Expressive\ActiveRecord\Result
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columns` | **string&#124;array** |  |





***

### first



```php
protected first(string|array $columns = &#039;*&#039;): ?\Qubus\Expressive\ActiveRecord\Row
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columns` | **string&#124;array** |  |





***

### find



```php
protected find(mixed $id): \Qubus\Expressive\ActiveRecord\Result|\Qubus\Expressive\ActiveRecord\Row|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$id` | **mixed** |  |





***

### pluck



```php
protected pluck(mixed $field): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$field` | **mixed** |  |





***

### create



```php
protected static create(array $data): bool|static|\Qubus\Expressive\Database|\Qubus\Expressive\QueryBuilder|int
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |




**Throws:**

- [`ReadOnlyException`](./Exception/ReadOnlyException.md)



***

### update



```php
protected update(array $data): bool|\Qubus\Expressive\Database|\Qubus\Expressive\QueryBuilder|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |




**Throws:**

- [`ReadOnlyException`](./Exception/ReadOnlyException.md)



***

### save



```php
protected save(): bool|int|\Qubus\Expressive\Database|\Qubus\Expressive\QueryBuilder
```











**Throws:**

- [`ReadOnlyException`](./Exception/ReadOnlyException.md)



***

### delete



```php
protected delete(): bool|\Qubus\Expressive\Database|\Qubus\Expressive\QueryBuilder|int
```











**Throws:**

- [`ReadOnlyException`](./Exception/ReadOnlyException.md)



***

### getPrimaryKey



```php
public getPrimaryKey(): string
```












***

### getData



```php
public getData(?string $field = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$field` | **?string** |  |





***

### setData



```php
public setData(mixed $field, mixed $value = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$field` | **mixed** |  |
| `$value` | **mixed** |  |





***

### toArray



```php
public toArray(): array
```












***

### toJson



```php
public toJson(): bool|string
```












***

### hasOne

======================================
Relationship Methods
======================================

```php
public hasOne(\Qubus\Expressive\ActiveRecord\Model|string $related, string|int|null $foreignKey = null): \Qubus\Expressive\ActiveRecord\Relations\HasOne
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$related` | **\Qubus\Expressive\ActiveRecord\Model&#124;string** |  |
| `$foreignKey` | **string&#124;int&#124;null** |  |





***

### hasMany



```php
public hasMany(\Qubus\Expressive\ActiveRecord\Model|string $related, string|int|null $foreignKey = null): \Qubus\Expressive\ActiveRecord\Relations\HasMany
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$related` | **\Qubus\Expressive\ActiveRecord\Model&#124;string** |  |
| `$foreignKey` | **string&#124;int&#124;null** |  |





***

### belongsTo



```php
public belongsTo(\Qubus\Expressive\ActiveRecord\Model|string $related, string|int|null $foreignKey = null): \Qubus\Expressive\ActiveRecord\Relations\BelongsTo
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$related` | **\Qubus\Expressive\ActiveRecord\Model&#124;string** |  |
| `$foreignKey` | **string&#124;int&#124;null** |  |





***

### belongsToMany



```php
public belongsToMany(\Qubus\Expressive\ActiveRecord\Model|string $related, ?string $pivotTable = null, string|int|null $foreignKey = null, string|int|null $otherKey = null): \Qubus\Expressive\ActiveRecord\Relations\BelongsToMany
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$related` | **\Qubus\Expressive\ActiveRecord\Model&#124;string** |  |
| `$pivotTable` | **?string** |  |
| `$foreignKey` | **string&#124;int&#124;null** |  |
| `$otherKey` | **string&#124;int&#124;null** |  |





***

### setRelation



```php
public setRelation(mixed $name, \Qubus\Expressive\ActiveRecord\Relations\Relation $relation): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |
| `$relation` | **\Qubus\Expressive\ActiveRecord\Relations\Relation** |  |





***

### getRelation



```php
public getRelation(mixed $name): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |





***

### load



```php
public load(string $related): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$related` | **string** |  |





***

### aggregates



```php
protected aggregates(mixed $function, mixed $field): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$function` | **mixed** |  |
| `$field` | **mixed** |  |





***

### max



```php
protected max(mixed $field): float|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$field` | **mixed** |  |





***

### min



```php
protected min(mixed $field): float|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$field` | **mixed** |  |





***

### avg



```php
protected avg(mixed $field): float|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$field` | **mixed** |  |





***

### sum



```php
protected sum(mixed $field): float|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$field` | **mixed** |  |





***

### count



```php
protected count(mixed $field = null): float|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$field` | **mixed** |  |





***

### setAttributesViaMassAssignment

======================================
Mass assignment protection.

```php
protected setAttributesViaMassAssignment(array|object $attributes): void
```

======================================






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attributes` | **array&#124;object** |  |





***

### timestamp



```php
protected timestamp(): void
```











**Throws:**

- [`Exception`](../../../Exception.md)



***

### isReadOnly



```php
private isReadOnly(string $methodName): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$methodName` | **string** |  |




**Throws:**

- [`ReadOnlyException`](./Exception/ReadOnlyException.md)



***

### __call

======================================
Magic Methods
======================================

```php
public __call(mixed $name, mixed $arguments): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |
| `$arguments` | **mixed** |  |





***

### __callStatic



```php
public static __callStatic(mixed $name, mixed $arguments): mixed
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |
| `$arguments` | **mixed** |  |





***

### __get



```php
public __get(mixed $field): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$field` | **mixed** |  |





***

### __set



```php
public __set(mixed $field, mixed $value): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$field` | **mixed** |  |
| `$value` | **mixed** |  |





***

### __isset



```php
public __isset(mixed $field): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$field` | **mixed** |  |





***


***
> Automatically generated on 2025-10-13
