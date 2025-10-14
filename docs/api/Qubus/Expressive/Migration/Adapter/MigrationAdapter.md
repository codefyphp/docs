***

# MigrationAdapter





* Full name: `\Qubus\Expressive\Migration\Adapter\MigrationAdapter`



## Methods


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












***

### createSchema

Create Schema

```php
public createSchema(): \Qubus\Expressive\Migration\Adapter\MigrationAdapter
```












***


***
> Automatically generated on 2025-10-13
