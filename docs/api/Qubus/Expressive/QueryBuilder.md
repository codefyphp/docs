# QueryBuilder

***

* Full name: `\Qubus\Expressive\QueryBuilder`
* This class implements:
  `IteratorAggregate`,
  `Stringable`,
  [`\Qubus\Expressive\Database`](./Database.md)

## Constants

| Constant       | Visibility | Type | Value  |
|----------------|------------|------|--------|
| `ORDERBY_ASC`  | public     |      | 'ASC'  |
| `ORDERBY_DESC` | public     |      | 'DESC' |
| `EOL`          | public     |      | "\n"   |
| `TAB`          | public     |      | "\t"   |
| `EOL_TAB`      | public     |      | "\n\t" |

## Properties

### connection

```php
protected \Qubus\Expressive\Connection $connection
```

***

### tableName

```php
protected ?string $tableName
```

***

### tableToken

```php
protected string $tableToken
```

***

### tableAlias

```php
protected string $tableAlias
```

***

### isSingle

```php
protected bool $isSingle
```

***

### pdoStmt

```php
protected ?\PDOStatement $pdoStmt
```

***

### selectFields

```php
protected array $selectFields
```

***

### joinSources

```php
protected array $joinSources
```

***

### limit

```php
protected ?int $limit
```

***

### offset

```php
protected ?int $offset
```

***

### orderBy

```php
protected string[] $orderBy
```

***

### groupBy

```php
protected string[] $groupBy
```

***

### whereParameters

```php
protected array $whereParameters
```

***

### whereConditions

```php
protected array $whereConditions
```

***

### andOrOperator

```php
protected string $andOrOperator
```

***

### having

```php
protected array $having
```

***

### returning

```php
protected ?string $returning
```

***

### upsert

```php
protected array|null $upsert
```

***

### wrapOpen

```php
protected bool $wrapOpen
```

***

### lastWrapPosition

```php
protected int $lastWrapPosition
```

***

### isFluentQuery

```php
protected bool $isFluentQuery
```

***

### pdoExecuted

```php
protected bool $pdoExecuted
```

***

### data

```php
protected array $data
```

***

### debugSqlQuery

```php
protected bool $debugSqlQuery
```

***

### sqlQuery

```php
protected string $sqlQuery
```

***

### sqlParameters

```php
protected array $sqlParameters
```

***

### dirtyFields

```php
protected string[] $dirtyFields
```

***

### referenceKeys

```php
protected array<int|string,array> $referenceKeys
```

***

### joinOn

```php
protected bool $joinOn
```

***

### references

```php
protected static array $references
```

* This property is **static**.

***

### tablePrefix

```php
protected ?string $tablePrefix
```

***

### schema

```php
protected ?\Qubus\Expressive\Schema $schema
```

***

### tableStructure

```php
public string[] $tableStructure
```

***

### lastResult

```php
private list<array<string,mixed>> $lastResult
```

***

## Methods

### __construct

Constructor & set the table structure

```php
public __construct(\Qubus\Expressive\Connection $connection, string|null $tablePrefix = null, string $primaryKeyName = 'id', string $foreignKeyName = '%s_id'): mixed
```

**Parameters:**

| Parameter         | Type                             | Description                                                                      |
|-------------------|----------------------------------|----------------------------------------------------------------------------------|
| `$connection`     | **\Qubus\Expressive\Connection** | Database connection.                                                             |
| `$tablePrefix`    | **string\|null**                 | Prefix of database tables.                                                       |
| `$primaryKeyName` | **string**                       | Structure: table primary key. If it's an array, it must be the structure         |
| `$foreignKeyName` | **string**                       | Structure: table foreignKeyName.
It can be like %s_id where %s is the table name |

***

### fromInstance

```php
public static fromInstance(\Qubus\Expressive\Connection $connection, string $primaryKeyName = 'id', ?string $tablePrefix = null): \Qubus\Expressive\Database
```

* This method is **static**.
**Parameters:**

| Parameter         | Type                             | Description |
|-------------------|----------------------------------|-------------|
| `$connection`     | **\Qubus\Expressive\Connection** |             |
| `$primaryKeyName` | **string**                       |             |
| `$tablePrefix`    | **?string**                      |             |

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

### getConnection

```php
public getConnection(): \Qubus\Expressive\Connection
```

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
public setTablePrefix(?string $tablePrefix = ''): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter      | Type        | Description |
|----------------|-------------|-------------|
| `$tablePrefix` | **?string** |             |

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

### isSingleRow

Return if the entry is of a single row

```php
public isSingleRow(): bool
```

***

### raw

```php
public raw(string $sql, array $params = []): list<array<string,mixed>>
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$sql`    | **string** |             |
| `$params` | **array**  |             |

***

### query

To execute a raw query

```php
public query(string $query, array $parameters = [], bool $returnAsPdoStmt = false): \Qubus\Expressive\Database|\PDOStatement
```

**Parameters:**

| Parameter          | Type       | Description                                                                                                                                |
|--------------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| `$query`           | **string** |                                                                                                                                            |
| `$parameters`      | **array**  |                                                                                                                                            |
| `$returnAsPdoStmt` | **bool**   | True, it will return the PDOStatement
false, it will return $this, which can be used for chaining
or access the properties of the results. |

***

### getResults

Retrieve an entire SQL result set from the database (i.e. many rows).

```php
public getResults(?string $query = null, string $output = \Qubus\Expressive\Database::OBJECT): false|string|array
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$query`  | **?string** |             |
| `$output` | **string**  |             |

**Throws:**

- [`JsonException`](../../JsonException.md)

***

### getVar

Retrieve one variable from the database.

```php
public getVar(?string $query = null, int $x = 0, int $y = 0): string|int|null
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$query`  | **?string** |             |
| `$x`      | **int**     |             |
| `$y`      | **int**     |             |

***

### getCol

Retrieve one column from the database.

```php
public getCol(?string $query = null, int $x = 0): array|null
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$query`  | **?string** |             |
| `$x`      | **int**     |             |

***

### getRow

Retrieve one row from the database.

```php
public getRow(?string $query = null, string $output = \Qubus\Expressive\Database::OBJECT, int $y = 0): object|array|null
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$query`  | **?string** |             |
| `$output` | **string**  |             |
| `$y`      | **int**     |             |

***

### rowCount

Return the number of affected row by the last statement

```php
public rowCount(): int
```

***

### find

To find all rows and create their instances
Use the query builder to build the where clause or $this->query with select
If a callback function is provided, the 1st arg must accept the rows results

```php
public find(?callable $callback = null): mixed
```

**Parameters:**

| Parameter   | Type          | Description                         |
|-------------|---------------|-------------------------------------|
| `$callback` | **?callable** | Run a function on the returned rows |

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

### getIterator

This method allow the iteration inside foreach().

```php
public getIterator(): \ArrayIterator
```

***

### fromArray

Create an instance from the given row (an associative
array of data fetched from the database).

```php
public fromArray(array $data): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **array** |             |

***

### select

Create the select clause.

```php
public select(mixed $columns = '*', ?string $alias = null): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter  | Type        | Description                                                |
|------------|-------------|------------------------------------------------------------|
| `$columns` | **mixed**   | The column(s) to select. Can be string or array of fields. |
| `$alias`   | **?string** | An alias to the column.                                    |

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
public whereIn(string $columnName, array $values): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description                                       |
|---------------|------------|---------------------------------------------------|
| `$columnName` | **string** |                                                   |
| `$values`     | **array**  | An empty list produces an always-false predicate. |

***

### whereNotIn

WHERE $columName NOT IN (?,?,?,...)

```php
public whereNotIn(string $columnName, array $values): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description                      |
|---------------|------------|----------------------------------|
| `$columnName` | **string** |                                  |
| `$values`     | **array**  | An empty list adds no predicate. |

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

### limit

LIMIT $limit

```php
public limit(?int $limit = null): \Qubus\Expressive\Database|int|null
```

**Parameters:**

| Parameter | Type     | Description                                                         |
|-----------|----------|---------------------------------------------------------------------|
| `$limit`  | **?int** | A non-negative limit, including zero; null reads the current limit. |

***

### offset

OFFSET $offset

```php
public offset(?int $offset = null): \Qubus\Expressive\Database|int|null
```

**Parameters:**

| Parameter | Type     | Description                                           |
|-----------|----------|-------------------------------------------------------|
| `$offset` | **?int** | A non-negative offset; null reads the current offset. |

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

### join

Build a join

```php
public join(string|\Qubus\Expressive\Database $tableName, string $constraint, string $tableAlias = '', string $joinOperator = \self::JOIN_LEFT): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter       | Type                                   | Description                   |
|-----------------|----------------------------------------|-------------------------------|
| `$tableName`    | **string\|\Qubus\Expressive\Database** |                               |
| `$constraint`   | **string**                             | -> id = profile.user_id       |
| `$tableAlias`   | **string**                             | - The alias of the table name |
| `$joinOperator` | **string**                             | - LEFT \| INNER \| etc...     |

***

### on

An alias to join by using a Database instance.

```php
public on(\Qubus\Expressive\Database $query, string $joinOperator = \self::JOIN_LEFT): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter       | Type                           | Description |
|-----------------|--------------------------------|-------------|
| `$query`        | **\Qubus\Expressive\Database** |             |
| `$joinOperator` | **string**                     |             |

***

### getSelectQuery

Return the built select query

```php
public getSelectQuery(): string
```

***

### schema

The associated schema instance.

```php
public schema(): \Qubus\Expressive\Schema
```

***

### getSelectString

Get the select fields as string for SQL.

```php
public getSelectString(): string
```

***

### getSelectFields

Return the select fields as array.

```php
public getSelectFields(): list<string>
```

***

### getJoinString

Get a JOIN string.

```php
public getJoinString(): string
```

***

### getGroupbyString

Get the group by string.

```php
public getGroupbyString(): string
```

***

### getOrderbyString

Get the order by string.

```php
public getOrderbyString(): string
```

***

### getWhereString

Build the WHERE clause(s).

```php
public getWhereString(): string
```

***

### getJoinOnString

Create the JOIN ... ON string when there is a join. It will be called by on().

```php
public getJoinOnString(): string
```

***

### getHavingString

Return the HAVING clause.

```php
protected getHavingString(): string
```

***

### getWhereParameters

Return the values to be bound for where.

```php
protected getWhereParameters(): array
```

***

### setSingleWhere

Detect if it's a single row instance and reset it to PK.

```php
protected setSingleWhere(): $this
```

***

### resetWhere

Reset the where.

```php
protected resetWhere(): $this
```

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
public upsert(array $conflictCols, array $updateData): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter       | Type      | Description |
|-----------------|-----------|-------------|
| `$conflictCols` | **array** |             |
| `$updateData`   | **array** |             |

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
public insert(array $data): \Qubus\Expressive\Database|int
```

**Parameters:**

| Parameter | Type      | Description     |
|-----------|-----------|-----------------|
| `$data`   | **array** | Data to insert. |

***

### update

Update entries.

```php
public update(?array $data = null): \Qubus\Expressive\Database|int|false
```

**Parameters:**

| Parameter | Type       | Description        |
|-----------|------------|--------------------|
| `$data`   | **?array** | the data to update |

***

### delete

Delete rows.

```php
public delete(bool $deleteAll = false): \Qubus\Expressive\Database|int|false
```

**Parameters:**

| Parameter    | Type     | Description                                                        |
|--------------|----------|--------------------------------------------------------------------|
| `$deleteAll` | **bool** | When there is no where condition, setting to true will delete all. |

***

### beginTransaction

Initiates a transaction.

```php
public beginTransaction(): bool
```

***

### inTransaction

Checks if inside transaction.

```php
public inTransaction(): bool
```

***

### commit

Commits a transaction

```php
public commit(): bool
```

***

### rollBack

Rolls back a transaction.

```php
public rollBack(): bool
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

***

### set

To set data for update or insert
$key can be an array for mass set

```php
public set(mixed $key, mixed $value = null): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$key`    | **mixed** |             |
| `$value`  | **mixed** |             |

***

### save

Save, a shortcut to update() or insert().

```php
public save(): \Qubus\Expressive\Database|int|bool
```

***

### count

Return the aggregate count of column

```php
public count(?string $column = null): float|int
```

**Parameters:**

| Parameter | Type        | Description       |
|-----------|-------------|-------------------|
| `$column` | **?string** | - the column name |

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

### getPK

Return the primary key.

```php
public getPK(): int|string|null
```

***

### get

Get the key

```php
public get(string $key): mixed
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### toArray

Return the raw data of this single instance.

```php
public toArray(): array
```

***

### __get

```php
public __get(mixed $key): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$key`    | **mixed** |             |

***

### __set

```php
public __set(mixed $key, mixed $value): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$key`    | **mixed** |             |
| `$value`  | **mixed** |             |

***

### __isset

```php
public __isset(mixed $key): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$key`    | **mixed** |             |

***

### __call

Association / Load

```php
public __call(string $tablename, array $args): mixed
```

__call() will load a table by association or return the table object itself

To dynamically call a table

$db = new QueryBuilder($myPDO);
on table 'users'
$Users = $db->table("users");

Or to call a table association
on table 'photos' where users can have many photos
$allMyPhotos = $Users->findOne(1234)->photos();

Association allow you to associate the current table with another by using
foreignKey and localKey. The data is eagerly loaded hence only making one round to the table
to retrieve the data matching the foreign and protected keys
foreign and protected keys are cached for subsequent queries,
the keys are selected based on the foreignKeyname pattern.
i.e: having the keys: id, user_id, friend_id, name, last_name
id, user_id, friend_id will be cached so they can be queried upon request

**Parameters:**

| Parameter    | Type       | Description                                            |
|--------------|------------|--------------------------------------------------------|
| `$tablename` | **string** |                                                        |
| `$args`      | **array**  | 
foreignKey
localKey
where
sort
callback
model
backref |

***

### reset

Reset fields

```php
public reset(): $this
```

***

### now

Return an Immutable YYYY-MM-DD HH:II:SS date format

```php
public static now(string $datetime = 'now'): string
```

* This method is **static**.
**Parameters:**

| Parameter   | Type       | Description                                                                                                                   |
|-------------|------------|-------------------------------------------------------------------------------------------------------------------------------|
| `$datetime` | **string** | - An english textual datetime description
now, yesterday, 3 days ago, +1 week
http://php.net/manual/en/function.strtotime.php |

**Return Value:**

YYYY-MM-DD HH:II:SS

**Throws:**

- [`Exception`](../../Exception.md)

***

### debugSqlQuery

To debug the query. It will not execute it but instead using debugSqlQuery()
and getSqlParameters to get the data

```php
public debugSqlQuery(bool $bool = true): $this
```

**Parameters:**

| Parameter | Type     | Description |
|-----------|----------|-------------|
| `$bool`   | **bool** |             |

***

### getSqlQuery

Get the SQL Query with

```php
public getSqlQuery(): string
```

***

### getSqlParameters

Return the parameters of the SQL

```php
public getSqlParameters(): array
```

***

### __toString

```php
public __toString(): string
```

***

### makePlaceholders

Return a string containing the given number of question marks,
separated by commas. Eg "?, ?, ?"

```php
protected makePlaceholders(int $numberOfPlaceholders = 1): string
```

**Parameters:**

| Parameter               | Type    | Description                       |
|-------------------------|---------|-----------------------------------|
| `$numberOfPlaceholders` | **int** | - total of placeholder to insert. |

***

### formatKeyname

Format the table{Primary\|Foreign}KeyName

```php
protected formatKeyname(string $pattern, string|null $tablename = null): string
```

**Parameters:**

| Parameter    | Type             | Description |
|--------------|------------------|-------------|
| `$pattern`   | **string**       |             |
| `$tablename` | **string\|null** |             |

***

### tokenize

To create a string that will be used as key for the relationship.

```php
protected tokenize(string $key, string $suffix = ''): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |
| `$suffix` | **string** |             |

***

### isArrayMultiDim

Check if array is multi dim.

```php
protected isArrayMultiDim(array $data): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **array** |             |

***

### prepareColumns

Prepare columns to include the table alias name.

```php
protected prepareColumns(array $columns): array
```

**Parameters:**

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `$columns` | **array** |             |

***

### prepareColumn

```php
protected prepareColumn(string $column): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$column` | **string** |             |

***

### formatColumnName

Format a column name to add to the table alias.

```php
public formatColumnName(string $column): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$column` | **string** |             |

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

### quotePreparedValue

```php
private quotePreparedValue(mixed $value): string
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

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

### execute

```php
private execute(string $sql, array<int|string,scalar|null> $params = []): \PDOStatement
```

**Parameters:**

| Parameter | Type                                | Description |
|-----------|-------------------------------------|-------------|
| `$sql`    | **string**                          |             |
| `$params` | **array<int\|string,scalar\|null>** |             |

***
