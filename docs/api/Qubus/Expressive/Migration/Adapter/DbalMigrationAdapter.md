***

# DbalMigrationAdapter





* Full name: `\Qubus\Expressive\Migration\Adapter\DbalMigrationAdapter`
* This class implements:
[`\Qubus\Expressive\Migration\Adapter\MigrationAdapter`](./MigrationAdapter.md)



## Properties


### connection



```php
protected \Qubus\Expressive\Connection $connection
```






***

### tableName



```php
protected string $tableName
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Expressive\Connection $connection, string $tableName): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$connection` | **\Qubus\Expressive\Connection** |  |
| `$tableName` | **string** |  |





***

### connection



```php
public connection(): \Qubus\Expressive\Connection
```












***

### fetchAll

Get all migrated version numbers

```php
public fetchAll(): array
```











**Throws:**

- [`Exception`](../../../../Exception.md)



***

### up

Up

```php
public up(\Qubus\Expressive\Migration\Migration $migration): \Qubus\Expressive\Migration\Adapter\MigrationAdapter
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$migration` | **\Qubus\Expressive\Migration\Migration** |  |





***

### down

Down

```php
public down(\Qubus\Expressive\Migration\Migration $migration): \Qubus\Expressive\Migration\Adapter\MigrationAdapter
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$migration` | **\Qubus\Expressive\Migration\Migration** |  |





***

### hasSchema

Is the schema ready?

```php
public hasSchema(): bool
```











**Throws:**

- [`Exception`](../../../../Exception.md)



***

### createSchema

Create Schema

```php
public createSchema(): \Qubus\Expressive\Migration\Adapter\MigrationAdapter
```











**Throws:**

- [`Exception`](../../../../Exception.md)



***


***
> Automatically generated on 2025-10-13
