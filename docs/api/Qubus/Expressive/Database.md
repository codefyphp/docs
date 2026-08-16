# Database

***

* Full name: `\Qubus\Expressive\Database`
* Parent interfaces:
  [`\Qubus\Expressive\Singleton`](./Singleton.md),
  [`\Qubus\Expressive\Table`](./Table.md),
  [`\Qubus\Expressive\Select`](./Select.md),
  [`\Qubus\Expressive\Where`](./Where.md),
  [`\Qubus\Expressive\Insert`](./Insert.md),
  [`\Qubus\Expressive\Update`](./Update.md),
  [`\Qubus\Expressive\Set`](./Set.md),
  [`\Qubus\Expressive\Delete`](./Delete.md),
  [`\Qubus\Expressive\Join`](./Join.md),
  [`\Qubus\Expressive\Aggregate`](./Aggregate.md)

## Constants


| Constant      | Visibility | Type | Value         |
|---------------|------------|------|---------------|
| `OBJECT`      | public     |      | 'OBJECT'      |
| `ARRAY_A`     | public     |      | 'ARRAY_A'     |
| `ARRAY_N`     | public     |      | 'ARRAY_N'     |
| `JSON_OBJECT` | public     |      | 'JSON_OBJECT' |

## Methods

### getConnection

```php
public getConnection(): \Qubus\Expressive\Connection
```

***

### schema

The associated schema instance.

```php
public schema(): \Qubus\Expressive\Schema
```

***

### transactional

Run transactional queries.

```php
public transactional(\Closure $callback, mixed $that = null, mixed $default = null): mixed
```

**Parameters:**

| Parameter   | Type         | Description          |
|-------------|--------------|----------------------|
| `$callback` | **\Closure** | transaction callback |
| `$that`     | **mixed**    |                      |
| `$default`  | **mixed**    |                      |

**Throws:**

- [`Exception`](../../Exception.md)

***

### prepare

Prepares positional or named placeholders in a query string.

```php
public prepare(string $query, mixed $params): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$query`  | **string** |             |
| `$params` | **mixed**  |             |

***

### quote

Wrapper for PDO::quote.

```php
public quote(string|array $value): false|string
```

**Parameters:**

| Parameter | Type              | Description |
|-----------|-------------------|-------------|
| `$value`  | **string\|array** |             |

**Return Value:**

Quoted string.

***

### raw

```php
public raw(string $sql, array<int|string,scalar|null> $params = []): list<array<string,mixed>>
```

**Parameters:**

| Parameter | Type                                | Description |
|-----------|-------------------------------------|-------------|
| `$sql`    | **string**                          |             |
| `$params` | **array<int\|string,scalar\|null>** |             |

***

### getResults

Retrieve an entire SQL result set from the database (i.e. many rows).

```php
public getResults(string|null $query = null, string $output = \self::OBJECT): false|string|array
```

**Parameters:**

| Parameter | Type             | Description |
|-----------|------------------|-------------|
| `$query`  | **string\|null** |             |
| `$output` | **string**       |             |

***

### getVar

Retrieve one variable from the database.

```php
public getVar(string|null $query = null, int $x = 0, int $y = 0): string|int|null
```

**Parameters:**

| Parameter | Type             | Description |
|-----------|------------------|-------------|
| `$query`  | **string\|null** |             |
| `$x`      | **int**          |             |
| `$y`      | **int**          |             |

***

### getCol

Retrieve one column from the database.

```php
public getCol(string|null $query = null, int $x = 0): array|null
```

**Parameters:**

| Parameter | Type             | Description |
|-----------|------------------|-------------|
| `$query`  | **string\|null** |             |
| `$x`      | **int**          |             |

***

### getRow

Retrieve one row from the database.

```php
public getRow(string|null $query = null, string $output = \self::OBJECT, int $y = 0): object|array|null
```

**Parameters:**

| Parameter | Type             | Description |
|-----------|------------------|-------------|
| `$query`  | **string\|null** |             |
| `$output` | **string**       |             |
| `$y`      | **int**          |             |

***

## Inherited methods

### count

Return the aggregate count of column

```php
public count(string|null $column = null): float|int
```

**Parameters:**

| Parameter | Type             | Description       |
|-----------|------------------|-------------------|
| `$column` | **string\|null** | - the column name |

***

### max

Return the aggregate max count of column

```php
public max(string $column): float|int
```

**Parameters:**

| Parameter | Type       | Description       |
|-----------|------------|-------------------|
| `$column` | **string** | - the column name |

***

### min

Return the aggregate min count of column

```php
public min(string $column): float|int
```

**Parameters:**

| Parameter | Type       | Description       |
|-----------|------------|-------------------|
| `$column` | **string** | - the column name |

***

### sum

Return the aggregate sum count of column

```php
public sum(string $column): float|int
```

**Parameters:**

| Parameter | Type       | Description       |
|-----------|------------|-------------------|
| `$column` | **string** | - the column name |

***

### avg

Return the aggregate average count of column

```php
public avg(string $column): float|int
```

**Parameters:**

| Parameter | Type       | Description       |
|-----------|------------|-------------------|
| `$column` | **string** | - the column name |

***

### aggregate

```php
public aggregate(string $fn): float|int
```

**Parameters:**

| Parameter | Type       | Description                               |
|-----------|------------|-------------------------------------------|
| `$fn`     | **string** | - The function to use for the aggregation |

***

### join

Build a join

```php
public join(string $tableName, string $constraint, string $tableAlias = '', string $joinOperator = \self::JOIN_LEFT): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter       | Type       | Description                   |
|-----------------|------------|-------------------------------|
| `$tableName`    | **string** |                               |
| `$constraint`   | **string** | -> id = profile.user_id       |
| `$tableAlias`   | **string** | - The alias of the table name |
| `$joinOperator` | **string** | - LEFT \| INNER \| etc...     |

***

### on

An alias to join by using a Database instance.

```php
public on(\Qubus\Expressive\Database $query, string $joinOperator = \self::JOIN_LEFT): \Qubus\Expressive\Database
```

The Database instance may have select and where statement for the ON clause

**Parameters:**

| Parameter       | Type                           | Description |
|-----------------|--------------------------------|-------------|
| `$query`        | **\Qubus\Expressive\Database** |             |
| `$joinOperator` | **string**                     |             |

***

### getJoinOnString

Create the JOIN ... ON string when there is a join. It will be called by on().

```php
public getJoinOnString(): string
```

***

### delete

Delete rows.

```php
public delete(bool $deleteAll = false): \Qubus\Expressive\Database|int|false
```

Use the query builder to create the where clause.

**Parameters:**

| Parameter    | Type     | Description                                                        |
|--------------|----------|--------------------------------------------------------------------|
| `$deleteAll` | **bool** | When there is no where condition, setting to true will delete all. |

***

### set

To set data for update or insert
$key can be an array for mass set

```php
public set(mixed $key, mixed|null $value = null): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$key`    | **mixed**       |             |
| `$value`  | **mixed\|null** |             |

***

### save

Save, a shortcut to update() or insert().

```php
public save(): \Qubus\Expressive\Database|int|bool
```

***

### update

Update entries.

```php
public update(array<string,mixed>|null $data = null): \Qubus\Expressive\Database|int|false
```

Use the query builder to create the where clause.

**Parameters:**

| Parameter | Type                          | Description        |
|-----------|-------------------------------|--------------------|
| `$data`   | **array<string,mixed>\|null** | the data to update |

***

### returning

Returning (Postgres etc.)

```php
public returning(string $cols = '*'): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$cols`   | **string** |             |

***

### upsert

Upsert (basic support)

```php
public upsert(list<string> $conflictCols, array<string,mixed> $updateData): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter       | Type                    | Description |
|-----------------|-------------------------|-------------|
| `$conflictCols` | **list<string>**        |             |
| `$updateData`   | **array<string,mixed>** |             |

***

### lastInsertId

Retrieves the ID of the last record inserted.

```php
public lastInsertId(string|null $pk = null): string|false
```

**Parameters:**

| Parameter | Type             | Description |
|-----------|------------------|-------------|
| `$pk`     | **string\|null** |             |

***

### insert

Insert one or more rows. Bulk rows must contain identical columns in identical order.

```php
public insert(array<string,mixed>|list<array<string,mixed>> $data): \Qubus\Expressive\Database|int
```

If a single row is inserted, its row instance is returned. Bulk inserts return the affected row count.

**Parameters:**

| Parameter | Type                                               | Description     |
|-----------|----------------------------------------------------|-----------------|
| `$data`   | **array<string,mixed>\|list<array<string,mixed>>** | Data to insert. |

**Throws:**

When the payload is empty or bulk rows have inconsistent columns.
- [`QueryBuilderException`](./QueryBuilderException.md)

***

### where

Add where condition, more calls appends with AND.

```php
public where(mixed $condition, mixed $parameters = null): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type      | Description                                                |
|---------------|-----------|------------------------------------------------------------|
| `$condition`  | **mixed** | condition possibly containing ? or :name                   |
| `$parameters` | **mixed** | array accepted by PDOStatement::execute or a scalar value. |

***

### wherePK

Where Primary key

```php
public wherePK(int|string $id): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$id`     | **int\|string** |             |

***

### whereNot

WHERE $columName != $value

```php
public whereNot(string $columnName, mixed $value): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |
| `$value`      | **mixed**  |             |

***

### whereLike

WHERE $columName LIKE $value

```php
public whereLike(string $columnName, mixed $value): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |
| `$value`      | **mixed**  |             |

***

### whereNotLike

WHERE $columName NOT LIKE $value

```php
public whereNotLike(string $columnName, mixed $value): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |
| `$value`      | **mixed**  |             |

***

### whereGt

WHERE $columName > $value

```php
public whereGt(string $columnName, mixed $value): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |
| `$value`      | **mixed**  |             |

***

### whereGte

WHERE $columName >= $value

```php
public whereGte(string $columnName, mixed $value): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |
| `$value`      | **mixed**  |             |

***

### whereLt

WHERE $columName < $value

```php
public whereLt(string $columnName, mixed $value): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |
| `$value`      | **mixed**  |             |

***

### whereLte

WHERE $columName <= $value

```php
public whereLte(string $columnName, mixed $value): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |
| `$value`      | **mixed**  |             |

***

### whereIn

WHERE $columName IN (?,?,?,...)

```php
public whereIn(string $columnName, list $values): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description                                       |
|---------------|------------|---------------------------------------------------|
| `$columnName` | **string** |                                                   |
| `$values`     | **list**   | An empty list produces an always-false predicate. |

***

### whereNotIn

WHERE $columName NOT IN (?,?,?,...)

```php
public whereNotIn(string $columnName, list $values): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description                      |
|---------------|------------|----------------------------------|
| `$columnName` | **string** |                                  |
| `$values`     | **list**   | An empty list adds no predicate. |

***

### whereNull

WHERE $columName IS NULL

```php
public whereNull(string $columnName): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |

***

### whereNotNull

WHERE $columName IS NOT NULL

```php
public whereNotNull(string $columnName): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |

***

### orderBy

ORDER BY $columnName (ASC \| DESC)

```php
public orderBy(string $columnName, string $ordering = 'ASC'): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description                              |
|---------------|------------|------------------------------------------|
| `$columnName` | **string** | - The name of the colum or an expression |
| `$ordering`   | **string** | `ASC` or `DESC`, case-insensitive.       |

**Throws:**

When the ordering is not `ASC` or `DESC`.
- [`QueryBuilderException`](./QueryBuilderException.md)

***

### limit

LIMIT $limit

```php
public limit(int|null $limit = null): \Qubus\Expressive\Database|int|null
```

**Parameters:**

| Parameter | Type          | Description                                                         |
|-----------|---------------|---------------------------------------------------------------------|
| `$limit`  | **int\|null** | A non-negative limit, including zero; null reads the current limit. |

***

### offset

OFFSET $offset

```php
public offset(int|null $offset = null): \Qubus\Expressive\Database|int|null
```

**Parameters:**

| Parameter | Type          | Description                                           |
|-----------|---------------|-------------------------------------------------------|
| `$offset` | **int\|null** | A non-negative offset; null reads the current offset. |

***

### pagination

```php
public pagination(int $perPage, int $page): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter  | Type    | Description |
|------------|---------|-------------|
| `$perPage` | **int** |             |
| `$page`    | **int** |             |

***

### and

Create an AND operator in the where clause

```php
public and(): \Qubus\Expressive\Database
```

***

### or

Create an OR operator in the where clause

```php
public or(): \Qubus\Expressive\Database
```

***

### wrap

To group multiple where clauses together.

```php
public wrap(): \Qubus\Expressive\Database
```

***

### query

To execute a raw query

```php
public query(string $query, array<int|string,mixed> $parameters = [], bool $returnAsPdoStmt = false): \Qubus\Expressive\Database|\PDOStatement
```

**Parameters:**

| Parameter          | Type                         | Description                                                                                                                                |
|--------------------|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| `$query`           | **string**                   |                                                                                                                                            |
| `$parameters`      | **array<int\|string,mixed>** |                                                                                                                                            |
| `$returnAsPdoStmt` | **bool**                     | True, it will return the PDOStatement
false, it will return $this, which can be used for chaining
or access the properties of the results. |

***

### find

To find all rows and create their instances
Use the query builder to build the where clause or $this->query with select
If a callback function is provided, the 1st arg must accept the rows results

```php
public find(callable|null $callback = null): mixed
```

$this->find(function($rows){
  // do more stuff here...
});

**Parameters:**

| Parameter   | Type               | Description                         |
|-------------|--------------------|-------------------------------------|
| `$callback` | **callable\|null** | Run a function on the returned rows |

**Return Value:**

The callback result, an iterator of rows, or false when no statement was executed.

***

### findOne

Return one row

```php
public findOne(int|string|null $id = null): \Qubus\Expressive\Database|false
```

**Parameters:**

| Parameter | Type                  | Description                  |
|-----------|-----------------------|------------------------------|
| `$id`     | **int\|string\|null** | Use to fetch by primary key. |

***

### select

Create the select clause.

```php
public select(mixed $columns = '*', string|null $alias = null): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter  | Type             | Description                                                |
|------------|------------------|------------------------------------------------------------|
| `$columns` | **mixed**        | The column(s) to select. Can be string or array of fields. |
| `$alias`   | **string\|null** | An alias to the column.                                    |

***

### getSelectFields

Return the select fields as array.

```php
public getSelectFields(): list<string>
```

***

### fromArray

Create an instance from the given row (an associative
array of data fetched from the database).

```php
public fromArray(array<string,mixed> $data): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter | Type                    | Description |
|-----------|-------------------------|-------------|
| `$data`   | **array<string,mixed>** |             |

***

### having

```php
public having(mixed $statement, string $operator = \self::OPERATOR_AND): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$statement` | **mixed**  |             |
| `$operator`  | **string** |             |

***

### groupBy

GROUP BY $columnName

```php
public groupBy(string $columnName): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |

***

### table

Define the working table and create a new instance

```php
public table(string $tableName, ?string $alias = null): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter    | Type        | Description           |
|--------------|-------------|-----------------------|
| `$tableName` | **string**  | Table name.           |
| `$alias`     | **?string** | The table alias name. |

***

### getTableName

Return the name of the table.

```php
public getTableName(): ?string
```

***

### setTableAlias

Set the table alias.

```php
public setTableAlias(string $alias): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$alias`  | **string** |             |

***

### getTableAlias

Get table Alias

```php
public getTableAlias(): string
```

***

### setStructure

```php
public setStructure(string $primaryKeyName = 'id', string $foreignKeyName = '%s_id'): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter         | Type       | Description                                                                           |
|-------------------|------------|---------------------------------------------------------------------------------------|
| `$primaryKeyName` | **string** | The primary key, ie: id                                                               |
| `$foreignKeyName` | **string** | The foreign key as a pattern: %s_id,
where %s will be substituted with the table name |

***

### setTablePrefix

```php
public setTablePrefix(string|null $tablePrefix = ''): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter      | Type             | Description |
|----------------|------------------|-------------|
| `$tablePrefix` | **string\|null** |             |

***

### getTablePrefix

Return the table prefix.

```php
public getTablePrefix(): ?string
```

***

### getStructure

Return the table structure.

```php
public getStructure(): array{primaryKeyname: string, foreignKeyname: string}
```

***

### getPrimaryKeyname

Get the primary key name.

```php
public getPrimaryKeyname(): string
```

***

### getForeignKeyname

Get foreign key name.

```php
public getForeignKeyname(): string
```

***

### fromInstance

```php
public static fromInstance(\Qubus\Expressive\Connection $connection, string $primaryKeyName = 'id', string|null $tablePrefix = null): \Qubus\Expressive\Database
```

* This method is **static**.
**Parameters:**

| Parameter         | Type                             | Description |
|-------------------|----------------------------------|-------------|
| `$connection`     | **\Qubus\Expressive\Connection** |             |
| `$primaryKeyName` | **string**                       |             |
| `$tablePrefix`    | **string\|null**                 |             |

***
