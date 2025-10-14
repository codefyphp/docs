***

# CachingDecorator





* Full name: `\Codefy\CommandBus\Decorators\CachingDecorator`
* This class implements:
[`\Codefy\CommandBus\Decorator`](../Decorator.md)



## Properties


### cache



```php
protected \Psr\Cache\CacheItemPoolInterface $cache
```






***

### expiresAfter



```php
protected int $expiresAfter
```






***

### innerBus



```php
protected \Codefy\CommandBus\CommandBus $innerBus
```






***

## Methods


### __construct



```php
public __construct(\Psr\Cache\CacheItemPoolInterface $cache, int $expiresAfter, \Codefy\CommandBus\CommandBus $innerBus): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$cache` | **\Psr\Cache\CacheItemPoolInterface** |  |
| `$expiresAfter` | **int** |  |
| `$innerBus` | **\Codefy\CommandBus\CommandBus** |  |





***

### setInnerBus

Set the CommandBus which we're decorating.

```php
public setInnerBus(\Codefy\CommandBus\CommandBus $bus): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$bus` | **\Codefy\CommandBus\CommandBus** |  |





***

### execute

Execute a command

```php
public execute(\Codefy\CommandBus\Command $command): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$command` | **\Codefy\CommandBus\Command** |  |




**Throws:**

- [`InvalidArgumentException`](../../../Psr/Cache/InvalidArgumentException.md)



***

### createCacheItem

Create a new cache item to be persisted.

```php
private createCacheItem(\Codefy\CommandBus\CacheableCommand $command, mixed $value): \Psr\Cache\CacheItemInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$command` | **\Codefy\CommandBus\CacheableCommand** |  |
| `$value` | **mixed** |  |




**Throws:**

- [`InvalidArgumentException`](../../../Psr/Cache/InvalidArgumentException.md)



***

### getCacheKey

Create the key to be used when saving this item to the cache pool.

```php
private getCacheKey(\Codefy\CommandBus\CacheableCommand $command): string|null
```

The cache item key is taken as a (string) serialized command, to ensure the return value is unique
depending on the command properties; that serialized string is then md5'd to ensure it doesn't
overflow any string length limits the implementing CacheItemPoolInterface library has.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$command` | **\Codefy\CommandBus\CacheableCommand** |  |





***

### getCacheExpiry

Determine when this CachableCommand should expire, in terms of seconds from now.

```php
private getCacheExpiry(\Codefy\CommandBus\CacheableCommand $command): int|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$command` | **\Codefy\CommandBus\CacheableCommand** |  |





***


***
> Automatically generated on 2025-10-13
