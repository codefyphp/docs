# Compiler

***

* Full name: `\Qubus\Expressive\Schema\Compiler`

## Properties

### separator

```php
protected string $separator
```

***

### wrapper

```php
protected string $wrapper
```

***

### params

```php
protected array $params
```

***

### modifiers

```php
protected string[] $modifiers
```

***

### serials

```php
protected string[] $serials
```

***

### autoincrement

```php
protected string $autoincrement
```

***

### connection

```php
protected \Qubus\Expressive\Connection $connection
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Expressive\Connection $connection): mixed
```

**Parameters:**

| Parameter     | Type                             | Description |
|---------------|----------------------------------|-------------|
| `$connection` | **\Qubus\Expressive\Connection** |             |

***

### setOptions

```php
public setOptions(array $options): $this
```

**Parameters:**

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `$options` | **array** |             |

***

### wrap

```php
protected wrap(string $name): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### wrapArray

```php
protected wrapArray(string[] $value, string $separator = ', '): string
```

**Parameters:**

| Parameter    | Type         | Description |
|--------------|--------------|-------------|
| `$value`     | **string[]** |             |
| `$separator` | **string**   |             |

***

### value

```php
protected value(float|bool|int|string|null $value): float|int|string
```

**Parameters:**

| Parameter | Type                               | Description |
|-----------|------------------------------------|-------------|
| `$value`  | **float\|bool\|int\|string\|null** |             |

***

### handleColumns

```php
protected handleColumns(\Qubus\Expressive\Schema\BaseColumn[] $columns): string
```

**Parameters:**

| Parameter  | Type                                      | Description |
|------------|-------------------------------------------|-------------|
| `$columns` | **\Qubus\Expressive\Schema\BaseColumn[]** |             |

***

### handleColumnType

```php
protected handleColumnType(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleColumnModifiers

```php
protected handleColumnModifiers(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleTypeInteger

```php
protected handleTypeInteger(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleTypeFloat

```php
protected handleTypeFloat(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleTypeDouble

```php
protected handleTypeDouble(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleTypeDecimal

```php
protected handleTypeDecimal(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleTypeBoolean

```php
protected handleTypeBoolean(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleTypeBinary

```php
protected handleTypeBinary(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleTypeText

```php
protected handleTypeText(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleTypeString

```php
protected handleTypeString(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleTypeFixed

```php
protected handleTypeFixed(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleTypeTime

```php
protected handleTypeTime(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleTypeTimestamp

```php
protected handleTypeTimestamp(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleTypeDate

```php
protected handleTypeDate(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleTypeDateTime

```php
protected handleTypeDateTime(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleModifierUnsigned

```php
protected handleModifierUnsigned(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleModifierNullable

```php
protected handleModifierNullable(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleModifierDefault

```php
protected handleModifierDefault(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handleModifierAutoincrement

```php
protected handleModifierAutoincrement(\Qubus\Expressive\Schema\BaseColumn $column): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$column` | **\Qubus\Expressive\Schema\BaseColumn** |             |

***

### handlePrimaryKey

```php
protected handlePrimaryKey(\Qubus\Expressive\Schema\CreateTable $schema): string
```

**Parameters:**

| Parameter | Type                                     | Description |
|-----------|------------------------------------------|-------------|
| `$schema` | **\Qubus\Expressive\Schema\CreateTable** |             |

***

### handleUniqueKeys

```php
protected handleUniqueKeys(\Qubus\Expressive\Schema\CreateTable $schema): string
```

**Parameters:**

| Parameter | Type                                     | Description |
|-----------|------------------------------------------|-------------|
| `$schema` | **\Qubus\Expressive\Schema\CreateTable** |             |

***

### handleIndexKeys

```php
protected handleIndexKeys(\Qubus\Expressive\Schema\CreateTable $schema): string[]
```

**Parameters:**

| Parameter | Type                                     | Description |
|-----------|------------------------------------------|-------------|
| `$schema` | **\Qubus\Expressive\Schema\CreateTable** |             |

***

### handleForeignKeys

```php
protected handleForeignKeys(\Qubus\Expressive\Schema\CreateTable $schema): string
```

**Parameters:**

| Parameter | Type                                     | Description |
|-----------|------------------------------------------|-------------|
| `$schema` | **\Qubus\Expressive\Schema\CreateTable** |             |

***

### handleEngine

```php
protected handleEngine(\Qubus\Expressive\Schema\CreateTable $schema): string
```

**Parameters:**

| Parameter | Type                                     | Description |
|-----------|------------------------------------------|-------------|
| `$schema` | **\Qubus\Expressive\Schema\CreateTable** |             |

***

### handleDropPrimaryKey

```php
protected handleDropPrimaryKey(\Qubus\Expressive\Schema\AlterTable $table, mixed $data): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$table`  | **\Qubus\Expressive\Schema\AlterTable** |             |
| `$data`   | **mixed**                               |             |

***

### handleDropUniqueKey

```php
protected handleDropUniqueKey(\Qubus\Expressive\Schema\AlterTable $table, mixed $data): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$table`  | **\Qubus\Expressive\Schema\AlterTable** |             |
| `$data`   | **mixed**                               |             |

***

### handleDropIndex

```php
protected handleDropIndex(\Qubus\Expressive\Schema\AlterTable $table, mixed $data): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$table`  | **\Qubus\Expressive\Schema\AlterTable** |             |
| `$data`   | **mixed**                               |             |

***

### handleDropForeignKey

```php
protected handleDropForeignKey(\Qubus\Expressive\Schema\AlterTable $table, mixed $data): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$table`  | **\Qubus\Expressive\Schema\AlterTable** |             |
| `$data`   | **mixed**                               |             |

***

### handleDropColumn

```php
protected handleDropColumn(\Qubus\Expressive\Schema\AlterTable $table, mixed $data): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$table`  | **\Qubus\Expressive\Schema\AlterTable** |             |
| `$data`   | **mixed**                               |             |

***

### handleRenameColumn

```php
protected handleRenameColumn(\Qubus\Expressive\Schema\AlterTable $table, mixed $data): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$table`  | **\Qubus\Expressive\Schema\AlterTable** |             |
| `$data`   | **mixed**                               |             |

***

### handleModifyColumn

```php
protected handleModifyColumn(\Qubus\Expressive\Schema\AlterTable $table, mixed $data): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$table`  | **\Qubus\Expressive\Schema\AlterTable** |             |
| `$data`   | **mixed**                               |             |

***

### handleAddColumn

```php
protected handleAddColumn(\Qubus\Expressive\Schema\AlterTable $table, mixed $data): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$table`  | **\Qubus\Expressive\Schema\AlterTable** |             |
| `$data`   | **mixed**                               |             |

***

### handleAddPrimary

```php
protected handleAddPrimary(\Qubus\Expressive\Schema\AlterTable $table, mixed $data): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$table`  | **\Qubus\Expressive\Schema\AlterTable** |             |
| `$data`   | **mixed**                               |             |

***

### handleAddUnique

```php
protected handleAddUnique(\Qubus\Expressive\Schema\AlterTable $table, mixed $data): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$table`  | **\Qubus\Expressive\Schema\AlterTable** |             |
| `$data`   | **mixed**                               |             |

***

### handleAddIndex

```php
protected handleAddIndex(\Qubus\Expressive\Schema\AlterTable $table, mixed $data): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$table`  | **\Qubus\Expressive\Schema\AlterTable** |             |
| `$data`   | **mixed**                               |             |

***

### handleAddForeign

```php
protected handleAddForeign(\Qubus\Expressive\Schema\AlterTable $table, mixed $data): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$table`  | **\Qubus\Expressive\Schema\AlterTable** |             |
| `$data`   | **mixed**                               |             |

***

### handleSetDefaultValue

```php
protected handleSetDefaultValue(\Qubus\Expressive\Schema\AlterTable $table, mixed $data): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$table`  | **\Qubus\Expressive\Schema\AlterTable** |             |
| `$data`   | **mixed**                               |             |

***

### handleDropDefaultValue

```php
protected handleDropDefaultValue(\Qubus\Expressive\Schema\AlterTable $table, mixed $data): string
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$table`  | **\Qubus\Expressive\Schema\AlterTable** |             |
| `$data`   | **mixed**                               |             |

***

### getParams

```php
public getParams(): array
```

***

### currentDatabase

```php
public currentDatabase(string|null $dsn = null): array
```

**Parameters:**

| Parameter | Type             | Description |
|-----------|------------------|-------------|
| `$dsn`    | **string\|null** |             |

***

### renameTable

```php
public renameTable(string $current, string $new): array
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$current` | **string** |             |
| `$new`     | **string** |             |

***

### getTables

```php
public getTables(string $database): array
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$database` | **string** |             |

***

### getColumns

```php
public getColumns(string $database, string $table): array
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$database` | **string** |             |
| `$table`    | **string** |             |

***

### create

```php
public create(\Qubus\Expressive\Schema\CreateTable $schema): array
```

**Parameters:**

| Parameter | Type                                     | Description |
|-----------|------------------------------------------|-------------|
| `$schema` | **\Qubus\Expressive\Schema\CreateTable** |             |

***

### alter

```php
public alter(\Qubus\Expressive\Schema\AlterTable $schema): array
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$schema` | **\Qubus\Expressive\Schema\AlterTable** |             |

***

### drop

```php
public drop(string $table): array
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$table`  | **string** |             |

***

### truncate

```php
public truncate(string $table): array
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$table`  | **string** |             |

***
