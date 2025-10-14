***

# Schema





* Full name: `\Qubus\Expressive\Schema`



## Properties


### connection



```php
protected ?\Qubus\Expressive\Connection $connection
```






***

### tableList



```php
protected array|null $tableList
```






***

### currentDatabase



```php
protected ?string $currentDatabase
```






***

### columns



```php
protected array $columns
```






***

## Methods


### __construct

Constructor.

```php
public __construct(\Qubus\Expressive\Connection $connection): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$connection` | **\Qubus\Expressive\Connection** | Connection. |





***

### getCurrentDatabase

Get the name of the currently used database.

```php
public getCurrentDatabase(): string
```











**Throws:**

- [`Exception`](../Exception/Exception.md)



***

### hasTable

Check if the specified table exists.

```php
public hasTable(string $table, bool $clear = false): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$table` | **string** | Table name. |
| `$clear` | **bool** | (optional) Refresh table list. |




**Throws:**

- [`Exception`](../Exception/Exception.md)



***

### getTables

Get a list with all tables that belong to the currently used database.

```php
public getTables(bool $clear = false): string[]
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$clear` | **bool** | (optional) Refresh table list. |




**Throws:**

- [`Exception`](../Exception/Exception.md)



***

### getColumns

Get a list with all columns that belong to the specified table.

```php
public getColumns(string $table, bool $clear = false, bool $names = true): false|string[]
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$table` | **string** |  |
| `$clear` | **bool** | (optional) Refresh column list. |
| `$names` | **bool** | (optional) Return only the column names. |




**Throws:**

- [`Exception`](../Exception/Exception.md)



***

### create

Creates a new table.

```php
public create(string $table, callable $callback): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$table` | **string** | Table name. |
| `$callback` | **callable** | A callback that will define table&#039;s fields and indexes. |




**Throws:**

- [`Exception`](../Exception/Exception.md)



***

### alter

Alters a table's definition.

```php
public alter(string $table, callable $callback): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$table` | **string** | Table name |
| `$callback` | **callable** | A callback that will add or remove fields or indexes. |




**Throws:**

- [`Exception`](../Exception/Exception.md)



***

### renameTable

Change a table's name.

```php
public renameTable(string $table, string $name): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$table` | **string** | The table. |
| `$name` | **string** | The new name of the table. |




**Throws:**

- [`Exception`](../Exception/Exception.md)



***

### drop

Deletes a table.

```php
public drop(string $table): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$table` | **string** | Table name. |




**Throws:**

- [`Exception`](../Exception/Exception.md)



***

### truncate

Deletes all records from a table.

```php
public truncate(string $table): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$table` | **string** | Table name. |




**Throws:**

- [`Exception`](../Exception/Exception.md)



***


***
> Automatically generated on 2025-10-13
