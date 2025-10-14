***

# ItemPool





* Full name: `\Qubus\Cache\Psr6\ItemPool`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Psr\Cache\CacheItemPoolInterface`](../../../Psr/Cache/CacheItemPoolInterface.md)
* This class is a **Final class**


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`CACHE_FLAG`|public| |&quot;@psr6_&quot;|

## Properties


### deferredItems



```php
protected \Psr\Cache\CacheItemInterface[] $deferredItems
```






***

### adapter



```php
private \Qubus\Cache\Adapter\CacheAdapter $adapter
```






***

### ttl



```php
private int|null|\DateInterval $ttl
```






***

### namespace



```php
private ?string $namespace
```






***

### autoCommitCount



```php
private ?int $autoCommitCount
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Cache\Adapter\CacheAdapter $adapter, int|null|\DateInterval $ttl = null, ?string $namespace = &#039;default&#039;, ?int $autoCommitCount = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$adapter` | **\Qubus\Cache\Adapter\CacheAdapter** |  |
| `$ttl` | **int&#124;null&#124;\DateInterval** |  |
| `$namespace` | **?string** |  |
| `$autoCommitCount` | **?int** |  |





***

### __destruct

Commit any pending deferred items.

```php
public __destruct(): mixed
```












***

### getItem

{@inheritdoc}

```php
public getItem(string $key): \Psr\Cache\CacheItemInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |





***

### getItems

{@inheritdoc}

```php
public getItems(array $keys = []): iterable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$keys` | **array** |  |





***

### hasItem

{@inheritdoc}

```php
public hasItem(string $key): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |





***

### clear

{@inheritdoc}

```php
public clear(): bool
```












***

### deleteItem

{@inheritdoc}

```php
public deleteItem(string $key): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |





***

### deleteItems

{@inheritdoc}

```php
public deleteItems(array $keys): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$keys` | **array** |  |





***

### save

{@inheritdoc}

```php
public save(\Psr\Cache\CacheItemInterface $item): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$item` | **\Psr\Cache\CacheItemInterface** |  |




**Throws:**

- [`InvalidArgumentException`](../../../Psr/Cache/InvalidArgumentException.md)



***

### saveDeferred

{@inheritdoc}

```php
public saveDeferred(\Psr\Cache\CacheItemInterface $item): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$item` | **\Psr\Cache\CacheItemInterface** |  |




**Throws:**

- [`TypeException`](../TypeException.md)



***

### commit

{@inheritdoc}

```php
public commit(): bool
```












***

### getTtl



```php
protected getTtl(int|null|\DateInterval $ttl): ?int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$ttl` | **int&#124;null&#124;\DateInterval** |  |





***


## Inherited methods


### reservedKeyCharacters

Reserved key characters that should not be used in a cache key.

```php
final public reservedKeyCharacters(): string
```





* This method is **final**.






***

### validateKey

Validates cache key.

```php
protected validateKey(string $key): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |




**Throws:**

- [`TypeException`](../TypeException.md)



***

### isHashed

Checks if key is hashed.

```php
protected isHashed(string $key): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |





***

### prefix

Affixes a prefix to the

```php
protected prefix(string $key): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |





***

### validateKeys

Validates an array of keys.

```php
protected validateKeys(array $keys): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$keys` | **array** |  |




**Throws:**

- [`TypeException`](../TypeException.md)



***


***
> Automatically generated on 2025-10-13
