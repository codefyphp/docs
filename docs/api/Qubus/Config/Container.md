***

# Container





* Full name: `\Qubus\Config\Container`
* This class implements:
[`\Psr\Container\ContainerInterface`](../../Psr/Container/ContainerInterface.md)



## Properties


### diContainer



```php
public \Psr\Container\ContainerInterface $diContainer
```






***

### container



```php
private array $container
```






***

### instances



```php
private array $instances
```






***

## Methods


### __construct



```php
public __construct(\Psr\Container\ContainerInterface $diContainer): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$diContainer` | **\Psr\Container\ContainerInterface** |  |





***

### get



```php
public get(mixed $id): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$id` | **mixed** |  |





***

### has



```php
public has(mixed $id): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$id` | **mixed** |  |





***

### getContainerValue



```php
protected getContainerValue(mixed $id): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$id` | **mixed** |  |





***

### add



```php
public add(mixed $alias, mixed $className, mixed $target = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$alias` | **mixed** |  |
| `$className` | **mixed** |  |
| `$target` | **mixed** |  |





***


***
> Automatically generated on 2025-10-13
