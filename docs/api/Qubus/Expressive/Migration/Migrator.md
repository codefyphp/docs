***

# Migrator





* Full name: `\Qubus\Expressive\Migration\Migrator`



## Properties


### objectmap



```php
protected ?\ArrayAccess $objectmap
```






***

### adapter



```php
protected ?\Qubus\Expressive\Migration\Adapter\MigrationAdapter $adapter
```






***

### output



```php
protected ?\Symfony\Component\Console\Output\OutputInterface $output
```






***

## Methods


### __construct

Constructor

```php
public __construct(\Qubus\Expressive\Migration\Adapter\MigrationAdapter $adapter, \ArrayAccess $objectmap, \Symfony\Component\Console\Output\OutputInterface $output): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$adapter` | **\Qubus\Expressive\Migration\Adapter\MigrationAdapter** |  |
| `$objectmap` | **\ArrayAccess** |  |
| `$output` | **\Symfony\Component\Console\Output\OutputInterface** |  |





***

### up

Run the up method on a migration

```php
public up(\Qubus\Expressive\Migration\Migration $migration): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$migration` | **\Qubus\Expressive\Migration\Migration** |  |





***

### down

Run the down method on a migration

```php
public down(\Qubus\Expressive\Migration\Migration $migration): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$migration` | **\Qubus\Expressive\Migration\Migration** |  |





***

### run

Run a migration in a particular direction

```php
protected run(\Qubus\Expressive\Migration\Migration $migration, string $direction = &#039;up&#039;): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$migration` | **\Qubus\Expressive\Migration\Migration** |  |
| `$direction` | **string** |  |





***

### getObjectMap

Get ObjectMap.

```php
public getObjectMap(): \ArrayAccess
```












***

### setObjectMap

Set ObjectMap.

```php
public setObjectMap(\ArrayAccess $objectmap): \Qubus\Expressive\Migration\Migrator
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$objectmap` | **\ArrayAccess** |  |





***

### getAdapter

Get Adapter

```php
public getAdapter(): \Qubus\Expressive\Migration\Adapter\MigrationAdapter|null
```












***

### setAdapter

Set Adapter

```php
public setAdapter(\Qubus\Expressive\Migration\Adapter\MigrationAdapter $adapter): \Qubus\Expressive\Migration\Migrator
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$adapter` | **\Qubus\Expressive\Migration\Adapter\MigrationAdapter** |  |





***

### getOutput

Get Output

```php
public getOutput(): \Symfony\Component\Console\Output\OutputInterface|null
```












***

### setOutput

Set Output

```php
public setOutput(\Symfony\Component\Console\Output\OutputInterface $output): \Qubus\Expressive\Migration\Migrator
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$output` | **\Symfony\Component\Console\Output\OutputInterface** |  |





***


***
> Automatically generated on 2025-10-13
