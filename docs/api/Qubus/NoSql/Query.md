***

# Query





* Full name: `\Qubus\NoSql\Query`


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`TYPE_GET`|public| |&#039;get&#039;|
|`TYPE_INSERT`|public| |&#039;insert&#039;|
|`TYPE_UPDATE`|public| |&#039;update&#039;|
|`TYPE_DELETE`|public| |&#039;delete&#039;|
|`TYPE_SAVE`|public| |&#039;save&#039;|

## Properties


### collection



```php
protected ?\Qubus\NoSql\Collection $collection
```






***

### pipes



```php
protected array $pipes
```






***

## Methods


### __construct



```php
public __construct(\Qubus\NoSql\Collection $collection): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$collection` | **\Qubus\NoSql\Collection** |  |





***

### getCollection



```php
public getCollection(): \Qubus\NoSql\Collection
```












***

### setCollection



```php
public setCollection(\Qubus\NoSql\Collection $collection): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$collection` | **\Qubus\NoSql\Collection** |  |





***

### where

Where filter.

```php
public where(mixed $filter): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$filter` | **mixed** |  |





***

### orWhere

Or where filter.

```php
public orWhere(mixed $filter): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$filter` | **mixed** |  |





***

### map



```php
public map(\Closure $mapper): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$mapper` | **\Closure** |  |





***

### select



```php
public select(array $columns): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columns` | **array** |  |





***

### withOne

1:1 relation

```php
public withOne(\Qubus\NoSql\Collection|\Qubus\NoSql\Query $relation, string $as, string $otherKey, string $operator = &#039;=&#039;, string $thisKey = &#039;_id&#039;): \Qubus\NoSql\Query
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$relation` | **\Qubus\NoSql\Collection&#124;\Qubus\NoSql\Query** |  |
| `$as` | **string** |  |
| `$otherKey` | **string** |  |
| `$operator` | **string** |  |
| `$thisKey` | **string** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### withMany

1:n relation

```php
public withMany(\Qubus\NoSql\Collection|\Qubus\NoSql\Query $relation, string $as, string $otherKey, string $operator = &#039;=&#039;, string $thisKey = &#039;_id&#039;): \Qubus\NoSql\Query
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$relation` | **\Qubus\NoSql\Collection&#124;\Qubus\NoSql\Query** |  |
| `$as` | **string** |  |
| `$otherKey` | **string** |  |
| `$operator` | **string** |  |
| `$thisKey` | **string** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### sortBy

Sort results.

```php
public sortBy(string|\Closure $key, string $asc = &#039;asc&#039;): \Qubus\NoSql\Query
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string&#124;\Closure** |  |
| `$asc` | **string** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### skip



```php
public skip(int $offset): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **int** |  |





***

### take



```php
public take(int $limit, int $offset): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$limit` | **int** |  |
| `$offset` | **int** |  |





***

### get

Fetching a set of records in collection.

```php
public get(array $select = []): mixed
```

If you want to retrieve a specific column define the column in the `$select` array.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$select` | **array** |  |





***

### first

Fetch (one) record in a collection.

```php
public first(array $select = []): mixed
```

If you want to retrieve a specific column(s) define the column in the `$select` array.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$select` | **array** |  |





***

### update



```php
public update(array $new): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$new` | **array** |  |




**Throws:**

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)

- [`TypeException`](../Exception/Data/TypeException.md)



***

### delete



```php
public delete(): mixed
```











**Throws:**

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)

- [`TypeException`](../Exception/Data/TypeException.md)



***

### save



```php
public save(): mixed
```











**Throws:**

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)

- [`TypeException`](../Exception/Data/TypeException.md)



***

### count



```php
public count(): int
```












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

### avg



```php
public avg(mixed $key): int|float
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |





***

### lists



```php
public lists(string $key, mixed $resultKey = null): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |
| `$resultKey` | **mixed** |  |





***

### pluck



```php
public pluck(string $key, mixed $resultKey = null): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |
| `$resultKey` | **mixed** |  |





***

### min



```php
public min(string $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |





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

### getPipes



```php
public getPipes(): array
```












***

### execute



```php
protected execute(string $type, array $arg = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$type` | **string** |  |
| `$arg` | **array** |  |




**Throws:**

- [`InvalidJsonException`](./Exceptions/InvalidJsonException.md)

- [`TypeException`](../Exception/Data/TypeException.md)



***

### addWhere



```php
protected addWhere(mixed $type, mixed $filter): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$type` | **mixed** |  |
| `$filter` | **mixed** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### addFilter



```php
protected addFilter(\Closure $filter, string $type = &#039;AND&#039;): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$filter` | **\Closure** |  |
| `$type` | **string** |  |





***

### addMapper



```php
protected addMapper(\Closure $mapper): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$mapper` | **\Closure** |  |





***

### addSorter



```php
protected addSorter(\Closure $value, string $asc): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **\Closure** |  |
| `$asc` | **string** |  |





***

### getLimiter



```php
protected getLimiter(): \Qubus\NoSql\Pipes\LimiterPipe
```












***

### addPipe



```php
protected addPipe(\Qubus\NoSql\Pipes\Pipe $pipe): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$pipe` | **\Qubus\NoSql\Pipes\Pipe** |  |





***

### getLastPipe



```php
protected getLastPipe(): mixed
```












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
