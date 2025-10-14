***

# Database





* Full name: `\Qubus\Expressive\Database`



## Methods


### table

Define the working table and create a new instance

```php
public table(string $tableName, ?string $alias = null): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$tableName` | **string** | Table name. |
| `$alias` | **?string** | The table alias name. |





***

### setStructure



```php
public setStructure(string $primaryKeyName = &#039;id&#039;, string $foreignKeyName = &#039;%s_id&#039;): \Qubus\Expressive\Database
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$primaryKeyName` | **string** | The primary key, ie: id |
| `$foreignKeyName` | **string** | The foreign key as a pattern: %s_id,<br />where %s will be substituted with the table name |





***

### query

To execute a raw query

```php
public query(string $query, array $parameters = [], bool $returnAsPdoStmt = false): \Qubus\Expressive\Database|\PDOStatement
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$query` | **string** |  |
| `$parameters` | **array** |  |
| `$returnAsPdoStmt` | **bool** | True, it will return the PDOStatement<br />false, it will return $this, which can be used for chaining<br />or access the properties of the results. |





***

### find

To find all rows and create their instances
Use the query builder to build the where clause or $this->query with select
If a callback function is provided, the 1st arg must accept the rows results

```php
public find(callable|null $callback = null): bool|\SplFixedArray|string|\ArrayIterator|\InternalIterator|array
```

$this->find(function($rows){
  // do more stuff here...
});






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **callable&#124;null** | Run a function on the returned rows |





***

### findOne

Return one row

```php
public findOne(int|string|null $id = null): \Qubus\Expressive\Database|false
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$id` | **int&#124;string&#124;null** | Use to fetch by primary key. |





***

### select

Create the select clause.

```php
public select(mixed $columns = &#039;*&#039;, string|null $alias = null): \Qubus\Expressive\Database
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columns` | **mixed** | The column(s) to select. Can be string or array of fields. |
| `$alias` | **string&#124;null** | An alias to the column. |





***

### where

Add where condition, more calls appends with AND.

```php
public where(mixed $condition, mixed $parameters = null): \Qubus\Expressive\Database
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$condition` | **mixed** | condition possibly containing ? or :name |
| `$parameters` | **mixed** | array accepted by PDOStatement::execute or a scalar value. |





***

### schema

The associated schema instance.

```php
public schema(): \Qubus\Expressive\Schema
```












***

### lastInsertId

Retrieves the ID of the last record inserted.

```php
public lastInsertId(string|null $pk = null): string|false
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$pk` | **string&#124;null** |  |





***

### insert

Insert new rows
$data can be 2-dimensional to add a bulk insert
If a single row is inserted, it will return its row instance

```php
public insert(array $data): \Qubus\Expressive\Database|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** | - data to populate |





***

### update

Update entries
Use the query builder to create the where clause.

```php
public update(array|null $data = null): \Qubus\Expressive\Database|int|false
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array&#124;null** | the data to update |





***

### delete

Delete rows.

```php
public delete(bool $deleteAll = false): \Qubus\Expressive\Database|int|false
```

Use the query builder to create the where clause.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$deleteAll` | **bool** | When there is no where condition, setting to true will delete all. |





***

### transactional

Run transactional queries.

```php
public transactional(\Closure $callback, mixed $that = null, mixed $default = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **\Closure** | transaction callback |
| `$that` | **mixed** |  |
| `$default` | **mixed** |  |




**Throws:**

- [`Exception`](../../Exception.md)



***


***
> Automatically generated on 2025-10-13
