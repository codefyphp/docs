***

# PdoConnection





* Full name: `\Qubus\Expressive\Connection\PdoConnection`
* This class implements:
[`\Qubus\Expressive\Connection`](../Connection.md)
* This class is an **Abstract class**



## Properties


### pdo



```php
public ?\PDO $pdo
```






***

### config



```php
protected array $config
```






***

### driver



```php
protected ?string $driver
```






***

### schemaCompiler



```php
protected ?\Qubus\Expressive\Schema\Compiler $schemaCompiler
```






***

### schema



```php
protected ?\Qubus\Expressive\Schema $schema
```






***

### schemaCompilerOptions



```php
protected array $schemaCompilerOptions
```






***

## Methods


### __construct



```php
public __construct(array $config): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$config` | **array** |  |





***

### createPdo



```php
protected createPdo(array $config): \PDO
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$config` | **array** |  |





***

### getDsn

Returns the DSN associated with this connection

```php
public getDsn(): string|null
```












***

### query

Execute a query

```php
public query(string $sql, array $params = []): \Qubus\Expressive\ResultSet
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$sql` | **string** | SQL Query. |
| `$params` | **array** | (optional) Query params. |





***

### command

Execute a non-query SQL command.

```php
public command(string $sql, array $params = []): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$sql` | **string** | SQL Command. |
| `$params` | **array** | (optional) Command params. |





***

### affectedRows

Execute a query and return the number of affected rows.

```php
public affectedRows(string $sql, array $params = []): int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$sql` | **string** | SQL Query. |
| `$params` | **array** | (optional) Query params. |





***

### column

Execute a query and fetch the first column

```php
public column(string $sql, array $params = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$sql` | **string** | SQL Query |
| `$params` | **array** | (optional) Query params |





***

### queryBuilder



```php
public queryBuilder(): \Qubus\Expressive\QueryBuilder
```












***

### getDriver

Returns the driver's name.

```php
public getDriver(): string|null
```












***

### getSchema

Returns the schema associated with this connection

```php
public getSchema(): \Qubus\Expressive\Schema
```












***

### schemaCompiler

Returns an instance of the schema compiler associated with this connection

```php
public schemaCompiler(): \Qubus\Expressive\Schema\Compiler
```











**Throws:**

- [`Exception`](../../../Exception.md)



***

### inTransaction



```php
public inTransaction(): bool
```












***

### startTransaction

Start a transaction.

```php
public startTransaction(): static
```












***

### commitTransaction



```php
public commitTransaction(): static
```












***

### rollbackTransaction



```php
public rollbackTransaction(): static
```












***

### transaction

Run transactional queries.

```php
public transaction(\Closure $callback, mixed $that = null, mixed $default = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **\Closure** | transaction callback |
| `$that` | **mixed** |  |
| `$default` | **mixed** |  |




**Throws:**

- [`Exception`](../../../Exception.md)



***

### setCharset

Sets the connection encoding.

```php
protected setCharset(string $charset): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$charset` | **string** | Encoding. |





***

### replaceParams

Replace placeholders with parameters.

```php
protected replaceParams(string $query, array $params): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$query` | **string** | SQL query |
| `$params` | **array** | Query parameters |





***

### prepare

Prepares a query.

```php
protected prepare(string $query, array $params): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$query` | **string** | SQL query |
| `$params` | **array** | Query parameters |





***

### bindValues



```php
protected bindValues(\PDOStatement $statement, array $values): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$statement` | **\PDOStatement** |  |
| `$values` | **array** |  |





***

### pdoExecute

Executes a prepared query and returns true on success or false on failure.

```php
protected pdoExecute(array $prepared): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$prepared` | **array** | Prepared query |





***

### supportsReturning



```php
public supportsReturning(): bool
```












***

### supportsUpsert



```php
public supportsUpsert(): bool
```












***

### supportsSavepoints



```php
public supportsSavepoints(): bool
```












***

### buildDsn



```php
public static buildDsn(array $config): string
```



* This method is **static**.
* This method is **abstract**.



**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$config` | **array** |  |





***


## Inherited methods


### quoteIdentifier



```php
public quoteIdentifier(string $identifier): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$identifier` | **string** |  |





***

### quote

Quote a value for an SQL query.

```php
public quote(float|array|bool|int|string|null $value = null): int|string
```

Objects passed to this function will be converted to strings.
Expression objects will use the value of the expression.
Query objects will be compiled and converted to a sub-query.
Fnc objects will be sent of for compiling.
All other objects will be converted using the `__toString` method.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **float&#124;array&#124;bool&#124;int&#124;string&#124;null** | any value to quote |





***


***
> Automatically generated on 2025-10-13
