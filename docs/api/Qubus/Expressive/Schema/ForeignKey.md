***

# ForeignKey





* Full name: `\Qubus\Expressive\Schema\ForeignKey`



## Properties


### refTable



```php
protected ?string $refTable
```






***

### refColumns



```php
protected string[] $refColumns
```






***

### actions



```php
protected array $actions
```






***

### columns



```php
protected string[] $columns
```






***

## Methods


### __construct



```php
public __construct(string[] $columns): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$columns` | **string[]** |  |





***

### addAction



```php
protected addAction(string $on, string $action): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$on` | **string** |  |
| `$action` | **string** |  |





***

### getReferencedTable



```php
public getReferencedTable(): string
```












***

### getReferencedColumns



```php
public getReferencedColumns(): string[]
```












***

### getColumns



```php
public getColumns(): string[]
```












***

### getActions



```php
public getActions(): array
```












***

### references



```php
public references(string $table, string[] $columns): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$table` | **string** |  |
| `$columns` | **string[]** |  |





***

### onDelete



```php
public onDelete(string $action): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$action` | **string** |  |





***

### onUpdate



```php
public onUpdate(string $action): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$action` | **string** |  |





***


***
> Automatically generated on 2025-10-13
