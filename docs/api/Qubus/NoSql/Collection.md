***

# Collection





* Full name: `\Qubus\NoSql\Collection`


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`KEY_ID`|public| |&#039;_id&#039;|
|`KEY_OLD_ID`|public| |&#039;_old&#039;|
|`UPDATING`|public| |&#039;updating&#039;|
|`UPDATED`|public| |&#039;updated&#039;|
|`INSERTING`|public| |&#039;inserting&#039;|
|`INSERTED`|public| |&#039;inserted&#039;|
|`DELETING`|public| |&#039;deleting&#039;|
|`DELETED`|public| |&#039;deleted&#039;|
|`CHANGED`|public| |&#039;changed&#039;|

## Properties


### filepath



```php
protected ?string $filepath
```






***

### resolver



```php
protected mixed $resolver
```






***

### events



```php
protected array $events
```






***

### transactionMode



```php
protected bool $transactionMode
```






***

### transactionData



```php
protected array|null $transactionData
```






***

### macros



```php
protected array $macros
```






***

### lastInsertId



```php
protected ?string $lastInsertId
```






***

### options



```php
private array|bool[]|int[]|string[] $options
```






***

## Methods


### __construct



```php
public __construct(string $filepath, array $options = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$filepath` | **string** |  |
| `$options` | **array** |  |





***

### macro



```php
public macro(string $name, callable $callback): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | Macro name. |
| `$callback` | **callable** |  |





***

### hasMacro

Check if macro exists.

```php
public hasMacro(string $name): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | Macro name. |





***

### getMacro

Return macro.

```php
public getMacro(string $name): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### getKeyId



```php
public getKeyId(): string
```












***

### getKeyOldId



```php
public getKeyOldId(): string
```












***

### isModeTransaction



```php
public isModeTransaction(): bool
```












***

### begin



```php
public begin(): void
```












***

### commit



```php
public commit(): bool|int
```












***

### rollback



```php
public rollback(): void
```












***

### transaction



```php
public transaction(callable $callback, mixed $that = null, mixed $default = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **callable** |  |
| `$that` | **mixed** |  |
| `$default` | **mixed** |  |




**Throws:**

- [`Exception`](../Exception/Exception.md)



***

### truncate



```php
public truncate(): bool|int
```












***

### on



```php
public on(string $event, callable $callback): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$event` | **string** | Event name. |
| `$callback` | **callable** |  |





***

### trigger



```php
protected trigger(string $event, array& $args): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$event` | **string** | Event name. |
| `$args` | **array** |  |





***

### loadData



```php
public loadData(): mixed
```











**Throws:**

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)



***

### setResolver



```php
public setResolver(callable $resolver): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$resolver` | **callable** |  |





***

### getResolver



```php
public getResolver(): mixed
```












***

### query



```php
public query(): \Qubus\NoSql\Query
```












***

### where



```php
public where(mixed $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |





***

### filter



```php
public filter(\Closure $closure): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$closure` | **\Closure** |  |





***

### map



```php
public map(\Closure $mapper): \Qubus\NoSql\Query
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$mapper` | **\Closure** |  |





***

### sortBy



```php
public sortBy(string $key, string $asc = &#039;asc&#039;): \Qubus\NoSql\Query
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |
| `$asc` | **string** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### sort



```php
public sort(\Closure $value): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **\Closure** |  |





***

### skip



```php
public skip(int $offset): \Qubus\NoSql\Query
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **int** |  |





***

### take



```php
public take(int $limit, int $offset): \Qubus\NoSql\Query
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$limit` | **int** |  |
| `$offset` | **int** |  |





***

### all



```php
public all(): array
```











**Throws:**

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)



***

### find



```php
public find(mixed $id): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$id` | **mixed** |  |




**Throws:**

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)



***

### lists



```php
public lists(mixed $key, mixed $resultKey = null): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |
| `$resultKey` | **mixed** |  |





***

### sum



```php
public sum(mixed $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |





***

### count



```php
public count(): ?int
```












***

### avg



```php
public avg(mixed $key): float|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |





***

### min



```php
public min(mixed $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |





***

### max



```php
public max(mixed $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |





***

### insert



```php
public insert(array $data): array|bool|int|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)



***

### inserts



```php
public inserts(array $listData): bool|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$listData` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)



***

### update



```php
public update(array $data): array|bool|int|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |




**Throws:**

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)

- [`TypeException`](../Exception/Data/TypeException.md)



***

### delete



```php
public delete(): array|bool|int|null
```











**Throws:**

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)

- [`TypeException`](../Exception/Data/TypeException.md)



***

### withOne

1:1 relation.

```php
public withOne(\Qubus\NoSql\Collection|\Qubus\NoSql\Query $relation, string $as, string $otherKey, string $operator = &#039;=&#039;, ?string $thisKey = null): \Qubus\NoSql\Query
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$relation` | **\Qubus\NoSql\Collection&#124;\Qubus\NoSql\Query** |  |
| `$as` | **string** |  |
| `$otherKey` | **string** |  |
| `$operator` | **string** |  |
| `$thisKey` | **?string** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### withMany

1:n relation.

```php
public withMany(\Qubus\NoSql\Collection|\Qubus\NoSql\Query $relation, string $as, string $otherKey, string $operator = &#039;=&#039;, ?string $thisKey = null): \Qubus\NoSql\Query
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$relation` | **\Qubus\NoSql\Collection&#124;\Qubus\NoSql\Query** |  |
| `$as` | **string** |  |
| `$otherKey` | **string** |  |
| `$operator` | **string** |  |
| `$thisKey` | **?string** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### generateKey



```php
public generateKey(): string
```












***

### execute



```php
public execute(\Qubus\NoSql\Query $query, string $type, array $arg = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$query` | **\Qubus\NoSql\Query** |  |
| `$type` | **string** |  |
| `$arg` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)



***

### executePipes



```php
protected executePipes(array $pipes): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$pipes` | **array** |  |




**Throws:**

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)



***

### executeInsert



```php
protected executeInsert(\Qubus\NoSql\Query $query, array $new = []): ?array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$query` | **\Qubus\NoSql\Query** |  |
| `$new` | **array** |  |




**Throws:**

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)

- [`TypeException`](../Exception/Data/TypeException.md)



***

### executeUpdate



```php
protected executeUpdate(\Qubus\NoSql\Query $query, array $new = []): bool|int|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$query` | **\Qubus\NoSql\Query** |  |
| `$new` | **array** |  |




**Throws:**

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)



***

### executeDelete



```php
protected executeDelete(\Qubus\NoSql\Query $query): bool|int|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$query` | **\Qubus\NoSql\Query** |  |




**Throws:**

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)



***

### executeGet



```php
protected executeGet(\Qubus\NoSql\Query $query): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$query` | **\Qubus\NoSql\Query** |  |




**Throws:**

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)



***

### executeSave



```php
protected executeSave(\Qubus\NoSql\Query $query): ?int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$query` | **\Qubus\NoSql\Query** |  |




**Throws:**

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)



***

### persists



```php
public persists(array $data): bool|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |





***

### save



```php
protected save(array $data): bool|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |





***

### lastInsertId

Returns the last insert id from the current document being acted upon.

```php
public lastInsertId(): ?string
```









**Return Value:**

The last insert id.




***

### __call



```php
public __call(mixed $method, mixed $args): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$method` | **mixed** |  |
| `$args` | **mixed** |  |




**Throws:**

- [`UndefinedMethodException`](./Exceptions/UndefinedMethodException.md)



***


***
> Automatically generated on 2025-10-13
