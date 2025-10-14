***

# CreateTable





* Full name: `\Qubus\Expressive\Schema\CreateTable`



## Properties


### columns



```php
protected \Qubus\Expressive\Schema\CreateColumn[] $columns
```






***

### primaryKey



```php
protected string|string[] $primaryKey
```






***

### uniqueKeys



```php
protected string[] $uniqueKeys
```






***

### indexes



```php
protected array $indexes
```






***

### foreignKeys



```php
protected array $foreignKeys
```






***

### table



```php
protected ?string $table
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

| Parameter | Type | Description |
|-----------|------|-------------|
| `$table` | **string** |  |





***

### addColumn



```php
protected addColumn(string $name, string $type): \Qubus\Expressive\Schema\CreateColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$type` | **string** |  |





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
public getPrimaryKey(): string|array|null
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
public getAutoincrement(): \Qubus\Expressive\Schema\BaseColumn
```












***

### engine



```php
public engine(string $name): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### primary



```php
public primary(string|string[] $columns, ?string $name = null): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columns` | **string&#124;string[]** |  |
| `$name` | **?string** |  |





***

### unique



```php
public unique(string|string[] $columns, ?string $name = null): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columns` | **string&#124;string[]** |  |
| `$name` | **?string** |  |





***

### index



```php
public index(string|string[] $columns, ?string $name = null): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columns` | **string&#124;string[]** |  |
| `$name` | **?string** |  |





***

### foreign



```php
public foreign(string|string[] $columns, ?string $name = null): \Qubus\Expressive\Schema\ForeignKey
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columns` | **string&#124;string[]** |  |
| `$name` | **?string** |  |





***

### autoincrement



```php
public autoincrement(\Qubus\Expressive\Schema\CreateColumn $column, ?string $name = null): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$column` | **\Qubus\Expressive\Schema\CreateColumn** |  |
| `$name` | **?string** |  |





***

### integer



```php
public integer(string $name): \Qubus\Expressive\Schema\CreateColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### float



```php
public float(string $name): \Qubus\Expressive\Schema\CreateColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### double



```php
public double(string $name): \Qubus\Expressive\Schema\CreateColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### decimal



```php
public decimal(string $name, ?int $length = null, ?int $precision = null): \Qubus\Expressive\Schema\CreateColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$length` | **?int** |  |
| `$precision` | **?int** |  |





***

### boolean



```php
public boolean(string $name): \Qubus\Expressive\Schema\CreateColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### binary



```php
public binary(string $name): \Qubus\Expressive\Schema\CreateColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### string



```php
public string(string $name, int $length = 255): \Qubus\Expressive\Schema\CreateColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$length` | **int** |  |





***

### fixed



```php
public fixed(string $name, int $length = 255): \Qubus\Expressive\Schema\CreateColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$length` | **int** |  |





***

### text



```php
public text(string $name): \Qubus\Expressive\Schema\CreateColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### time



```php
public time(string $name): \Qubus\Expressive\Schema\CreateColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### timestamp



```php
public timestamp(string $name): \Qubus\Expressive\Schema\CreateColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### date



```php
public date(string $name): \Qubus\Expressive\Schema\CreateColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### dateTime



```php
public dateTime(string $name): \Qubus\Expressive\Schema\CreateColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### softDelete



```php
public softDelete(string $column = &#039;deleted_at&#039;): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$column` | **string** |  |





***

### timestamps



```php
public timestamps(string $createColumn = &#039;created_at&#039;, string $updateColumn = &#039;updated_at&#039;): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$createColumn` | **string** |  |
| `$updateColumn` | **string** |  |





***


***
> Automatically generated on 2025-10-13
