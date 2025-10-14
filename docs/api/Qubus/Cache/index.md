
***

# Documentation



This is an automatically generated documentation for **Documentation**.


## Namespaces


### \Qubus\Cache

#### Classes

| Class | Description |
|-------|-------------|
| [`ApcuCache`](./ApcuCache.md) | |
| [`BaseCache`](./BaseCache.md) | |
| [`DateIntervalConverter`](./DateIntervalConverter.md) | |
| [`FileSystemCache`](./FileSystemCache.md) | |
| [`InMemoryCache`](./InMemoryCache.md) | |
| [`MemcachedCache`](./MemcachedCache.md) | |
| [`RedisCache`](./RedisCache.md) | |
| [`TypeException`](./TypeException.md) | |




### \Qubus\Cache\Adapter

#### Classes

| Class | Description |
|-------|-------------|
| [`ApcuCacheAdapter`](./Adapter/ApcuCacheAdapter.md) | |
| [`FileSystemCacheAdapter`](./Adapter/FileSystemCacheAdapter.md) | |
| [`InMemoryCacheAdapter`](./Adapter/InMemoryCacheAdapter.md) | |
| [`MemcachedCacheAdapter`](./Adapter/MemcachedCacheAdapter.md) | |
| [`Multiple`](./Adapter/Multiple.md) | |
| [`PredisCacheAdapter`](./Adapter/PredisCacheAdapter.md) | |
| [`RedisCacheAdapter`](./Adapter/RedisCacheAdapter.md) | |



#### Interfaces

| Interface | Description |
|-----------|-------------|
| [`CacheAdapter`](./Adapter/CacheAdapter.md) | |



### \Qubus\Cache\Psr16

#### Classes

| Class | Description |
|-------|-------------|
| [`SimpleCache`](./Psr16/SimpleCache.md) | |




### \Qubus\Cache\Psr6

#### Classes

| Class | Description |
|-------|-------------|
| [`Item`](./Psr6/Item.md) | |
| [`ItemPool`](./Psr6/ItemPool.md) | |
| [`TaggablePsr6PoolAdapter`](./Psr6/TaggablePsr6PoolAdapter.md) | This adapter lets you make any PSR-6 cache pool taggable. If a pool is<br />already taggable, it is simply returned by makeTaggable. Tags are stored<br />either in the same cache pool, or a separate pool, and both of these<br />approaches come with different caveats.|



#### Interfaces

| Interface | Description |
|-----------|-------------|
| [`TaggableCacheItem`](./Psr6/TaggableCacheItem.md) | An item that supports tags. This interface is a soon-to-be-PSR.|
| [`TaggableCacheItemPool`](./Psr6/TaggableCacheItemPool.md) | Interface for invalidating cached items using tags. This interface is a soon-to-be-PSR.|



### \Qubus\Cache\Traits



#### Traits

| Trait | Description |
|-------|-------------|
| [`ValidatableKeyAware`](./Traits/ValidatableKeyAware.md) | |




***
> Automatically generated on 2025-10-13
