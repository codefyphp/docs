***

# QueryBuilder





* Full name: `\Qubus\Expressive\QueryBuilder`
* This class implements:
[`\IteratorAggregate`](../../IteratorAggregate.md), [`\Stringable`](../../Stringable.md), [`\Qubus\Expressive\Database`](./Database.md)


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`OPERATOR_AND`|public| |&#039; AND &#039;|
|`OPERATOR_OR`|public| |&#039; OR &#039;|
|`ORDERBY_ASC`|public| |&#039;ASC&#039;|
|`ORDERBY_DESC`|public| |&#039;DESC&#039;|
|`JOIN_INNER`|public| |&#039;INNER&#039;|
|`JOIN_OUTER`|public| |&#039;OUTER&#039;|
|`JOIN_LEFT`|public| |&#039;LEFT&#039;|
|`JOIN_RIGHT`|public| |&#039;RIGHT&#039;|
|`JOIN_RIGHT_OUTER`|public| |&#039;RIGHT OUTER&#039;|
|`JOIN_LEFT_OUTER`|public| |&#039;LEFT OUTER&#039;|
|`EOL`|public| |&quot;\n&quot;|
|`TAB`|public| |&quot;\t&quot;|
|`EOL_TAB`|public| |&quot;\n\t&quot;|

## Properties


### instance



```php
protected static ?\Qubus\Expressive\QueryBuilder $instance
```



* This property is **static**.


***

### connection



```php
protected \Qubus\Expressive\Connection|null $connection
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
protected array $orderBy
```






***

### groupBy



```php
protected array $groupBy
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
protected ?array $upsert
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
protected array $dirtyFields
```






***

### referenceKeys



```php
protected array $referenceKeys
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
public array $tableStructure
```






***

## Methods


### __construct

Constructor & set the table structure

```php
public __construct(\Qubus\Expressive\Connection $connection, string|null $tablePrefix = null, string $primaryKeyName = &#039;id&#039;, string $foreignKeyName = &#039;%s_id&#039;): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$connection` | **\Qubus\Expressive\Connection** | Database connection. |
| `$tablePrefix` | **string&#124;null** | Prefix of database tables. |
| `$primaryKeyName` | **string** | Structure: table primary key. If it&#039;s an array, it must be the structure |
| `$foreignKeyName` | **string** | Structure: table foreignKeyName.<br />It can be like %s_id where %s is the table name |





***

### fromInstance



```php
public static fromInstance(\Qubus\Expressive\Connection $connection, string $primaryKeyName = &#039;id&#039;, ?string $tablePrefix = null): static
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$connection` | **\Qubus\Expressive\Connection** |  |
| `$primaryKeyName` | **string** |  |
| `$tablePrefix` | **?string** |  |





***

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

### getTableName

Return the name of the table.

```php
public getTableName(): string
```












***

### setTableAlias

Set the table alias.

```php
public setTableAlias(string $alias): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$alias` | **string** |  |





***

### getTableAlias

Get table Alias

```php
public getTableAlias(): string
```












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

### setTablePrefix



```php
public setTablePrefix(?string $tablePrefix = &#039;&#039;): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$tablePrefix` | **?string** |  |





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
public getStructure(): array
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
public find(?callable $callback = null): bool|\SplFixedArray|string|\ArrayIterator|\InternalIterator|array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **?callable** | Run a function on the returned rows |





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
public fromArray(array $data): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |





***

### select

Create the select clause.

```php
public select(mixed $columns = &#039;*&#039;, ?string $alias = null): \Qubus\Expressive\Database
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columns` | **mixed** | The column(s) to select. Can be string or array of fields. |
| `$alias` | **?string** | An alias to the column. |





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

### and

Create an AND operator in the where clause

```php
public and(): \Qubus\Expressive\QueryBuilder
```












***

### or

Create an OR operator in the where clause

```php
public or(): \Qubus\Expressive\QueryBuilder
```












***

### wrap

To group multiple where clauses together.

```php
public wrap(): \Qubus\Expressive\QueryBuilder
```












***

### wherePK

Where Primary key

```php
public wherePK(int|string $id): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$id` | **int&#124;string** |  |





***

### whereNot

WHERE $columName != $value

```php
public whereNot(string $columnName, mixed $value): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columnName` | **string** |  |
| `$value` | **mixed** |  |





***

### whereLike

WHERE $columName LIKE $value

```php
public whereLike(string $columnName, mixed $value): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columnName` | **string** |  |
| `$value` | **mixed** |  |





***

### whereNotLike

WHERE $columName NOT LIKE $value

```php
public whereNotLike(string $columnName, mixed $value): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columnName` | **string** |  |
| `$value` | **mixed** |  |





***

### whereGt

WHERE $columName > $value

```php
public whereGt(string $columnName, mixed $value): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columnName` | **string** |  |
| `$value` | **mixed** |  |





***

### whereGte

WHERE $columName >= $value

```php
public whereGte(string $columnName, mixed $value): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columnName` | **string** |  |
| `$value` | **mixed** |  |





***

### whereLt

WHERE $columName < $value

```php
public whereLt(string $columnName, mixed $value): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columnName` | **string** |  |
| `$value` | **mixed** |  |





***

### whereLte

WHERE $columName <= $value

```php
public whereLte(string $columnName, mixed $value): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columnName` | **string** |  |
| `$value` | **mixed** |  |





***

### whereIn

WHERE $columName IN (?,?,?,...)

```php
public whereIn(string $columnName, array $values): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columnName` | **string** |  |
| `$values` | **array** |  |





***

### whereNotIn

WHERE $columName NOT IN (?,?,?,...)

```php
public whereNotIn(string $columnName, array $values): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columnName` | **string** |  |
| `$values` | **array** |  |





***

### whereNull

WHERE $columName IS NULL

```php
public whereNull(string $columnName): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columnName` | **string** |  |





***

### whereNotNull

WHERE $columName IS NOT NULL

```php
public whereNotNull(string $columnName): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columnName` | **string** |  |





***

### having



```php
public having(mixed $statement, mixed $operator = self::OPERATOR_AND): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$statement` | **mixed** |  |
| `$operator` | **mixed** |  |





***

### orderBy

ORDER BY $columnName (ASC | DESC)

```php
public orderBy(string $columnName, string $ordering = &#039;&#039;): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columnName` | **string** | - The name of the colum or an expression |
| `$ordering` | **string** | (DESC &amp;#124; ASC) |





***

### groupBy

GROUP BY $columnName

```php
public groupBy(string $columnName): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columnName` | **string** |  |





***

### limit

LIMIT $limit

```php
public limit(int|null $limit = null): \Qubus\Expressive\QueryBuilder|int|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$limit` | **int&#124;null** |  |





***

### offset

OFFSET $offset

```php
public offset(int|null $offset = null): \Qubus\Expressive\QueryBuilder|int|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **int&#124;null** |  |





***

### pagination



```php
public pagination(int $perPage, int $page): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$perPage` | **int** |  |
| `$page` | **int** |  |





***

### join

Build a join

```php
public join(string $tableName, string $constraint, string $tableAlias = &#039;&#039;, string $joinOperator = self::JOIN_LEFT): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$tableName` | **string** |  |
| `$constraint` | **string** | -&gt; id = profile.user_id |
| `$tableAlias` | **string** | - The alias of the table name |
| `$joinOperator` | **string** | - LEFT &amp;#124; INNER &amp;#124; etc... |





***

### on

An alias to join by using a QueryBuilder instance.

```php
public on(\Qubus\Expressive\QueryBuilder $query, string $joinOperator = self::JOIN_LEFT): \Qubus\Expressive\QueryBuilder
```

The QueryBuilder instance may have select and where statement for the ON clause






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$query` | **\Qubus\Expressive\QueryBuilder** |  |
| `$joinOperator` | **string** |  |





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
public getSelectFields(): array
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
protected setSingleWhere(): \Qubus\Expressive\QueryBuilder
```












***

### resetWhere

Reset the where.

```php
protected resetWhere(): \Qubus\Expressive\QueryBuilder
```












***

### returning



```php
public returning(string $cols = &#039;*&#039;): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$cols` | **string** |  |





***

### upsert



```php
public upsert(array $conflictCols, array $updateData): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$conflictCols` | **array** |  |
| `$updateData` | **array** |  |





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
public update(?array $data = null): \Qubus\Expressive\Database|int|false
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **?array** | the data to update |





***

### delete

Delete rows.

```php
public delete(bool $deleteAll = false): \Qubus\Expressive\Database|int|false
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
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

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **\Closure** | transaction callback |
| `$that` | **mixed** |  |
| `$default` | **mixed** |  |





***

### set

To set data for update or insert
$key can be an array for mass set

```php
public set(mixed $key, mixed|null $value = null): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |
| `$value` | **mixed&#124;null** |  |





***

### save

Save, a shortcut to update() or insert().

```php
public save(): \Qubus\Expressive\QueryBuilder|int|bool|static
```












***

### count

Return the aggregate count of column

```php
public count(string|null $column = null): float|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$column` | **string&#124;null** | - the column name |





***

### max

Return the aggregate max count of column

```php
public max(string $column): float|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$column` | **string** | - the column name |





***

### min

Return the aggregate min count of column

```php
public min(string $column): float|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$column` | **string** | - the column name |





***

### sum

Return the aggregate sum count of column

```php
public sum(string $column): float|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$column` | **string** | - the column name |





***

### avg

Return the aggregate average count of column

```php
public avg(string $column): float|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$column` | **string** | - the column name |





***

### aggregate



```php
public aggregate(string $fn): float|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$fn` | **string** | - The function to use for the aggregation |





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

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |





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

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |





***

### __set



```php
public __set(mixed $key, mixed $value): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |
| `$value` | **mixed** |  |





***

### __isset



```php
public __isset(mixed $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |





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

| Parameter | Type | Description |
|-----------|------|-------------|
| `$tablename` | **string** |  |
| `$args` | **array** | <br />foreignKey<br />localKey<br />where<br />sort<br />callback<br />model<br />backref |





***

### reset

Reset fields

```php
public reset(): \Qubus\Expressive\QueryBuilder
```












***

### now

Return an Immutable YYYY-MM-DD HH:II:SS date format

```php
public static now(string $datetime = &#039;now&#039;): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$datetime` | **string** | - An english textual datetime description<br />now, yesterday, 3 days ago, +1 week<br />http://php.net/manual/en/function.strtotime.php |


**Return Value:**

YYYY-MM-DD HH:II:SS



**Throws:**

- [`Exception`](../../Exception.md)



***

### debugSqlQuery

To debug the query. It will not execute it but instead using debugSqlQuery()
and getSqlParameters to get the data

```php
public debugSqlQuery(bool $bool = true): \Qubus\Expressive\QueryBuilder
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$bool` | **bool** |  |





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

### __clone



```php
public __clone(): mixed
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

| Parameter | Type | Description |
|-----------|------|-------------|
| `$numberOfPlaceholders` | **int** | - total of placeholder to insert. |





***

### formatKeyname

Format the table{Primary|Foreign}KeyName

```php
protected formatKeyname(string $pattern, string $tablename): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$pattern` | **string** |  |
| `$tablename` | **string** |  |





***

### tokenize

To create a string that will be used as key for the relationship.

```php
protected tokenize(string $key, string $suffix = &#039;&#039;): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |
| `$suffix` | **string** |  |





***

### isArrayMultiDim

Check if array is multi dim.

```php
protected isArrayMultiDim(array $data): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |





***

### prepareColumns

Prepare columns to include the table alias name.

```php
protected prepareColumns(array $columns): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columns` | **array** |  |





***

### prepareColumn



```php
protected prepareColumn(string $column): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$column` | **string** |  |





***

### formatColumnName

Format a column name to add to the table alias.

```php
public formatColumnName(string $column): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$column` | **string** |  |





***


***
> Automatically generated on 2025-10-13
