***

# PdoDataMapper





* Full name: `\Qubus\Expressive\DataMapper\PdoDataMapper`
* This class implements:
[`\Qubus\Expressive\DataMapper\DataMapper`](./DataMapper.md)



## Properties


### entity



```php
protected string $entity
```






***

### table



```php
protected string $table
```






***

### columns



```php
protected array $columns
```






***

### connection



```php
public \Qubus\Expressive\Connection $connection
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Expressive\Connection $connection, string $entity): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$connection` | **\Qubus\Expressive\Connection** |  |
| `$entity` | **string** |  |




**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

- [`DataMapperException`](./DataMapperException.md)



***

### getPdo



```php
public getPdo(): \PDO|null
```












***

### queryBuilder



```php
public queryBuilder(): \Qubus\Expressive\QueryBuilder
```












***

### hydrate



```php
public hydrate(array $data): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |





***

### findAll



```php
public findAll(string $orderBy = &#039;&#039;, array $options = []): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$orderBy` | **string** |  |
| `$options` | **array** |  |





***

### findAllBy



```php
public findAllBy(string $column, string $value, string $orderBy = &#039;&#039;, array $options = []): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$column` | **string** |  |
| `$value` | **string** |  |
| `$orderBy` | **string** |  |
| `$options` | **array** |  |





***

### findOne



```php
public findOne(int|string $id): ?\Qubus\Expressive\DataMapper\SerializableEntity
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$id` | **int&#124;string** |  |





***

### create



```php
public create(\Qubus\Expressive\DataMapper\SerializableEntity $entity): \Qubus\Expressive\DataMapper\SerializableEntity
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$entity` | **\Qubus\Expressive\DataMapper\SerializableEntity** |  |





***

### update



```php
public update(\Qubus\Expressive\DataMapper\SerializableEntity $entity): \Qubus\Expressive\DataMapper\SerializableEntity
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$entity` | **\Qubus\Expressive\DataMapper\SerializableEntity** |  |





***

### delete



```php
public delete(int|string $id): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$id` | **int&#124;string** |  |





***

### buildSelectString



```php
private buildSelectString(): string
```












***

### buildOrderByString



```php
private buildOrderByString(string $orderBy, string $direction = &#039;ASC&#039;): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$orderBy` | **string** |  |
| `$direction` | **string** |  |





***

### buildLimitOffsetString



```php
private buildLimitOffsetString(int $limit, int $offset): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$limit` | **int** |  |
| `$offset` | **int** |  |





***

### buildInsertString



```php
private buildInsertString(): string
```












***

### buildUpdateString



```php
private buildUpdateString(): string
```












***

### buildDeleteString



```php
private buildDeleteString(): string
```












***

### mapRowToObject



```php
private mapRowToObject(array $row): \Qubus\Expressive\DataMapper\SerializableEntity
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$row` | **array** |  |





***


***
> Automatically generated on 2025-10-13
