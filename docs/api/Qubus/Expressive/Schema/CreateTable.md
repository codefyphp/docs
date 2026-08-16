# CreateTable

***

* Full name: `\Qubus\Expressive\Schema\CreateTable`

## Properties

### columns

```php
protected \Qubus\Expressive\Schema\CreateColumn[] $columns
```

***

### primaryKey

```php
protected array{name: string, columns: list<string>}|null $primaryKey
```

***

### uniqueKeys

```php
protected array<string,list<string>> $uniqueKeys
```

***

### indexes

```php
protected array<string,list<string>> $indexes
```

***

### foreignKeys

```php
protected array<string,\Qubus\Expressive\Schema\ForeignKey> $foreignKeys
```

***

### table

```php
protected string $table
```

***

### engine

```php
protected string|null $engine
```

***

### autoincrement

```php
protected ?\Qubus\Expressive\Schema\BaseColumn $autoincrement
```

***

## Methods

### __construct

```php
public __construct(string $table): mixed
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$table`  | **string** |             |

***

### addColumn

```php
protected addColumn(string $name, string $type): \Qubus\Expressive\Schema\CreateColumn
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |
| `$type`   | **string** |             |

***

### getTableName

```php
public getTableName(): string
```

***

### getColumns

```php
public getColumns(): \Qubus\Expressive\Schema\CreateColumn[]
```

***

### getPrimaryKey

```php
public getPrimaryKey(): array{name: string, columns: list<string>}|null
```

***

### getUniqueKeys

```php
public getUniqueKeys(): array
```

***

### getIndexes

```php
public getIndexes(): array
```

***

### getForeignKeys

```php
public getForeignKeys(): array
```

***

### getEngine

```php
public getEngine(): string|null
```

***

### getAutoincrement

```php
public getAutoincrement(): \Qubus\Expressive\Schema\BaseColumn|null
```

***

### engine

```php
public engine(string $name): $this
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### primary

```php
public primary(string|string[] $columns, ?string $name = null): $this
```

**Parameters:**

| Parameter  | Type                 | Description |
|------------|----------------------|-------------|
| `$columns` | **string\|string[]** |             |
| `$name`    | **?string**          |             |

***

### unique

```php
public unique(string|string[] $columns, ?string $name = null): $this
```

**Parameters:**

| Parameter  | Type                 | Description |
|------------|----------------------|-------------|
| `$columns` | **string\|string[]** |             |
| `$name`    | **?string**          |             |

***

### index

```php
public index(string|string[] $columns, ?string $name = null): $this
```

**Parameters:**

| Parameter  | Type                 | Description |
|------------|----------------------|-------------|
| `$columns` | **string\|string[]** |             |
| `$name`    | **?string**          |             |

***

### foreign

```php
public foreign(string|string[] $columns, ?string $name = null): \Qubus\Expressive\Schema\ForeignKey
```

**Parameters:**

| Parameter  | Type                 | Description |
|------------|----------------------|-------------|
| `$columns` | **string\|string[]** |             |
| `$name`    | **?string**          |             |

***

### autoincrement

```php
public autoincrement(\Qubus\Expressive\Schema\CreateColumn $column, ?string $name = null): $this
```

**Parameters:**

| Parameter | Type                                      | Description |
|-----------|-------------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\CreateColumn** |             |
| `$name`   | **?string**                               |             |

***

### integer

```php
public integer(string $name): \Qubus\Expressive\Schema\CreateColumn
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### float

```php
public float(string $name): \Qubus\Expressive\Schema\CreateColumn
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### double

```php
public double(string $name): \Qubus\Expressive\Schema\CreateColumn
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### decimal

```php
public decimal(string $name, ?int $length = null, ?int $precision = null): \Qubus\Expressive\Schema\CreateColumn
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$name`      | **string** |             |
| `$length`    | **?int**   |             |
| `$precision` | **?int**   |             |

***

### boolean

```php
public boolean(string $name): \Qubus\Expressive\Schema\CreateColumn
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### binary

```php
public binary(string $name): \Qubus\Expressive\Schema\CreateColumn
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### string

```php
public string(string $name, int $length = 255): \Qubus\Expressive\Schema\CreateColumn
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |
| `$length` | **int**    |             |

***

### fixed

```php
public fixed(string $name, int $length = 255): \Qubus\Expressive\Schema\CreateColumn
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |
| `$length` | **int**    |             |

***

### text

```php
public text(string $name): \Qubus\Expressive\Schema\CreateColumn
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### time

```php
public time(string $name): \Qubus\Expressive\Schema\CreateColumn
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### timestamp

```php
public timestamp(string $name): \Qubus\Expressive\Schema\CreateColumn
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### date

```php
public date(string $name): \Qubus\Expressive\Schema\CreateColumn
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### dateTime

```php
public dateTime(string $name): \Qubus\Expressive\Schema\CreateColumn
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### softDelete

```php
public softDelete(string $column = 'deleted_at'): $this
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$column` | **string** |             |

***

### timestamps

```php
public timestamps(string $createColumn = 'created_at', string $updateColumn = 'updated_at'): $this
```

**Parameters:**

| Parameter       | Type       | Description |
|-----------------|------------|-------------|
| `$createColumn` | **string** |             |
| `$updateColumn` | **string** |             |

***
