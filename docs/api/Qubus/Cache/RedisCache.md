***

# RedisCache





* Full name: `\Qubus\Cache\RedisCache`
* Parent class: [`\Qubus\Cache\BaseCache`](./BaseCache.md)
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**




## Methods


### __construct



```php
public __construct(\Redis $redis, int|null|\DateInterval $ttl = null, ?string $namespace = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$redis` | **\Redis** |  |
| `$ttl` | **int&#124;null&#124;\DateInterval** |  |
| `$namespace` | **?string** |  |





***


## Inherited methods


### __construct



```php
public __construct(int|null|\DateInterval $ttl = null, ?string $namespace = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$ttl` | **int&#124;null&#124;\DateInterval** |  |
| `$namespace` | **?string** |  |





***

### get

{@inheritdoc}

```php
public get(string $key, mixed $default = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |
| `$default` | **mixed** |  |





**See Also:**

* \Psr\SimpleCache\CacheInterface::get() - 

***

### set

{@inheritdoc}

```php
public set(string $key, mixed $value, null|int|\DateInterval $ttl = null): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |
| `$value` | **mixed** |  |
| `$ttl` | **null&#124;int&#124;\DateInterval** |  |





**See Also:**

* \Psr\SimpleCache\CacheInterface::set() - 

***

### delete

{@inheritdoc}

```php
public delete(string $key): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |





**See Also:**

* \Psr\SimpleCache\CacheInterface::delete() - 

***

### clear

{@inheritdoc}

```php
public clear(): bool
```












**See Also:**

* \Psr\SimpleCache\CacheInterface::clear() - * \Psr\Cache\CacheInterface::clear() - * \Qubus\Cache\Psr16\Psr16Cache::clear() - 

***

### getMultiple

{@inheritdoc}

```php
public getMultiple(iterable $keys, mixed $default = null): iterable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$keys` | **iterable** |  |
| `$default` | **mixed** |  |





**See Also:**

* \Psr\SimpleCache\CacheInterface::getMultiple() - 

***

### setMultiple

{@inheritdoc}

```php
public setMultiple(iterable $values, null|int|\DateInterval $ttl = null): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$values` | **iterable** |  |
| `$ttl` | **null&#124;int&#124;\DateInterval** |  |





**See Also:**

* \Psr\SimpleCache\CacheInterface::setMultiple() - 

***

### deleteMultiple

{@inheritdoc}

```php
public deleteMultiple(iterable $keys): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$keys` | **iterable** |  |





**See Also:**

* \Psr\SimpleCache\CacheInterface::deleteMultiple() - 

***

### has

{@inheritdoc}

```php
public has(string $key): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |





**See Also:**

* \Psr\SimpleCache\CacheInterface::has() - 

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





**See Also:**

* \Psr\Cache\CacheItemPoolInterface::getItem() - 

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





**See Also:**

* \Psr\Cache\CacheItemPoolInterface::getItems() - 

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





**See Also:**

* \Psr\Cache\CacheItemPoolInterface::hasItem() - 

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





**See Also:**

* \Psr\Cache\CacheItemPoolInterface::deleteItem() - 

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





**See Also:**

* \Psr\Cache\CacheItemPoolInterface::deleteItems() - 

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

- [`InvalidArgumentException`](../../Psr/Cache/InvalidArgumentException.md)



**See Also:**

* \Psr\Cache\CacheItemPoolInterface::save() - 

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

- [`TypeException`](./TypeException.md)



**See Also:**

* \Psr\Cache\CacheItemPoolInterface::saveDeferred() - 

***

### commit

{@inheritdoc}

```php
public commit(): bool
```












**See Also:**

* \Psr\Cache\CacheItemPoolInterface::commit() - 

***


***
> Automatically generated on 2025-10-13
