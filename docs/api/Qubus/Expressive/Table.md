# Table

***

* Full name: `\Qubus\Expressive\Table`

## Methods

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
