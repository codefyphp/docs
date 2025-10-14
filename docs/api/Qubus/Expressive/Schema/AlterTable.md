***

# AlterTable





* Full name: `\Qubus\Expressive\Schema\AlterTable`



## Properties


### table



```php
protected ?string $table
```






***

### commands



```php
protected array $commands
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

### addCommand



```php
protected addCommand(string $name, mixed $data): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$data` | **mixed** |  |





***

### addKey



```php
protected addKey(string $type, string|string[] $columns, ?string $name = null): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$type` | **string** |  |
| `$columns` | **string&#124;string[]** |  |
| `$name` | **?string** |  |





***

### addColumn



```php
protected addColumn(string $name, string $type): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$type` | **string** |  |





***

### modifyColumn



```php
protected modifyColumn(string $column, string $type): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$column` | **string** |  |
| `$type` | **string** |  |





***

### getTableName



```php
public getTableName(): string
```












***

### getCommands



```php
public getCommands(): array
```












***

### dropIndex



```php
public dropIndex(string $name): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### dropUnique



```php
public dropUnique(string $name): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### dropPrimary



```php
public dropPrimary(string $name): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### dropForeign



```php
public dropForeign(string $name): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### dropColumn



```php
public dropColumn(string $name): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### dropDefaultValue



```php
public dropDefaultValue(string $column): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$column` | **string** |  |





***

### renameColumn



```php
public renameColumn(string $from, string $to): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$from` | **string** |  |
| `$to` | **string** |  |





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

### setDefaultValue



```php
public setDefaultValue(string $column, mixed $value): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$column` | **string** |  |
| `$value` | **mixed** |  |





***

### integer



```php
public integer(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### float



```php
public float(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### double



```php
public double(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### decimal



```php
public decimal(string $name, ?int $length = null, ?int $precision = null): \Qubus\Expressive\Schema\AlterColumn
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
public boolean(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### binary



```php
public binary(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### string



```php
public string(string $name, int $length = 255): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$length` | **int** |  |





***

### fixed



```php
public fixed(string $name, int $length = 255): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$length` | **int** |  |





***

### text



```php
public text(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### time



```php
public time(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### timestamp



```php
public timestamp(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### date



```php
public date(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### dateTime



```php
public dateTime(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### toInteger



```php
public toInteger(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### toFloat



```php
public toFloat(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### toDouble



```php
public toDouble(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### toDecimal



```php
public toDecimal(string $name, ?int $length = null, ?int $precision = null): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$length` | **?int** |  |
| `$precision` | **?int** |  |





***

### toBoolean



```php
public toBoolean(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### toBinary



```php
public toBinary(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### toString



```php
public toString(string $name, int $length = 255): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$length` | **int** |  |





***

### toFixed



```php
public toFixed(string $name, int $length = 255): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$length` | **int** |  |





***

### toText



```php
public toText(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### toTime



```php
public toTime(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### toTimestamp



```php
public toTimestamp(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### toDate



```php
public toDate(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### toDateTime



```php
public toDateTime(string $name): \Qubus\Expressive\Schema\AlterColumn
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***


***
> Automatically generated on 2025-10-13
