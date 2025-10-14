***

# FileMigrationAdapter





* Full name: `\Qubus\Expressive\Migration\Adapter\FileMigrationAdapter`
* This class implements:
[`\Qubus\Expressive\Migration\Adapter\MigrationAdapter`](./MigrationAdapter.md)



## Properties


### filename



```php
protected string $filename
```






***

## Methods


### __construct



```php
public __construct(string $filename): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$filename` | **string** |  |





***

### fetchAll

Get all migrated version numbers

```php
public fetchAll(): array
```












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




**Throws:**

- [`TypeException`](../../../Exception/Data/TypeException.md)



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




**Throws:**

- [`TypeException`](../../../Exception/Data/TypeException.md)



***

### hasSchema

Is the schema ready?

```php
public hasSchema(): bool
```












***

### createSchema

Create Schema

```php
public createSchema(): \Qubus\Expressive\Migration\Adapter\MigrationAdapter
```











**Throws:**

- [`TypeException`](../../../Exception/Data/TypeException.md)



***

### write

Write to file

```php
protected write(array $versions): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$versions` | **array** |  |




**Throws:**

- [`TypeException`](../../../Exception/Data/TypeException.md)



***


***
> Automatically generated on 2025-10-13
