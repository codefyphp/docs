# TaggablePsr6PoolAdapter

This adapter lets you make any PSR-6 cache pool taggable. If a pool is
already taggable, it is simply returned by makeTaggable. Tags are stored
either in the same cache pool, or a separate pool, and both of these
approaches come with different caveats.

A general caveat is that using this adapter reserves any cache key starting
with '__tag.'.

Using the same pool is precarious if your cache does LRU evictions of items
even if they do not expire (as in e.g. memcached). If so, the tag item may
be evicted without all the tagged items having been evicted first,
causing items to lose their tags.

In order to mitigate this issue, you may use a separate, more persistent
pool for your tag items. Do however note that if you are doing so, the
entire pool is reserved for tags, as this pool is cleared whenever the
main pool is cleared.

***

* Full name: `\Qubus\Cache\Psr6\TaggablePsr6PoolAdapter`
* This class is marked as **final** and can't be subclassed
* This class implements:
  [`\Qubus\Cache\Psr6\TaggableCacheItemPool`](./TaggableCacheItemPool.md)
* This class is a **Final class**

## Properties

### cachePool

```php
private \Psr\Cache\CacheItemPoolInterface $cachePool
```

***

### tagStorePool

```php
private ?\Psr\Cache\CacheItemPoolInterface $tagStorePool
```

***

## Methods

### __construct

```php
private __construct(\Psr\Cache\CacheItemPoolInterface $cachePool, ?\Psr\Cache\CacheItemPoolInterface $tagStorePool = null): mixed
```

**Parameters:**

| Parameter       | Type                                   | Description |
|-----------------|----------------------------------------|-------------|
| `$cachePool`    | **\Psr\Cache\CacheItemPoolInterface**  |             |
| `$tagStorePool` | **?\Psr\Cache\CacheItemPoolInterface** |             |

***

### makeTaggable

```php
public static makeTaggable(\Psr\Cache\CacheItemPoolInterface $cachePool, \Psr\Cache\CacheItemPoolInterface|null $tagStorePool = null): \Qubus\Cache\Psr6\TaggableCacheItemPool
```

* This method is **static**.
**Parameters:**

| Parameter       | Type                                        | Description                                                          |
|-----------------|---------------------------------------------|----------------------------------------------------------------------|
| `$cachePool`    | **\Psr\Cache\CacheItemPoolInterface**       | The pool to which to add tagging capabilities                        |
| `$tagStorePool` | **\Psr\Cache\CacheItemPoolInterface\|null** | The pool to store tags in. If null is passed,
the main pool is used. |

***

### getItem

{@inheritdoc}

```php
public getItem(mixed $key): \Qubus\Cache\Psr6\TaggableCacheItem
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$key`    | **mixed** |             |

***

### getItems

{@inheritdoc}

```php
public getItems(array $keys = []): iterable
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$keys`   | **array** |             |

***

### hasItem

{@inheritdoc}

```php
public hasItem(string $key): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

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

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### deleteItems

{@inheritdoc}

```php
public deleteItems(array $keys): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$keys`   | **array** |             |

***

### save

{@inheritdoc}

```php
public save(\Qubus\Cache\Psr6\TaggableCacheItem|\Psr\Cache\CacheItemInterface $item): bool
```

**Parameters:**

| Parameter | Type                                                                   | Description |
|-----------|------------------------------------------------------------------------|-------------|
| `$item`   | **\Qubus\Cache\Psr6\TaggableCacheItem\|\Psr\Cache\CacheItemInterface** |             |

**Throws:**

- [`InvalidArgumentException`](../../../Psr/Cache/InvalidArgumentException.md)

***

### saveDeferred

{@inheritdoc}

```php
public saveDeferred(\Qubus\Cache\Psr6\TaggableCacheItem|\Psr\Cache\CacheItemInterface $item): bool
```

**Parameters:**

| Parameter | Type                                                                   | Description |
|-----------|------------------------------------------------------------------------|-------------|
| `$item`   | **\Qubus\Cache\Psr6\TaggableCacheItem\|\Psr\Cache\CacheItemInterface** |             |

**Throws:**

- [`InvalidArgumentException`](../../../Psr/Cache/InvalidArgumentException.md)

***

### commit

{@inheritdoc}

```php
public commit(): bool
```

***

### appendListItem

```php
protected appendListItem(mixed $name, mixed $value): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$name`   | **mixed** |             |
| `$value`  | **mixed** |             |

**Throws:**

- [`InvalidArgumentException`](../../../Psr/Cache/InvalidArgumentException.md)

***

### removeList

```php
protected removeList(mixed $name): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$name`   | **mixed** |             |

**Throws:**

- [`InvalidArgumentException`](../../../Psr/Cache/InvalidArgumentException.md)

***

### removeListItem

```php
protected removeListItem(mixed $name, mixed $key): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$name`   | **mixed** |             |
| `$key`    | **mixed** |             |

**Throws:**

- [`InvalidArgumentException`](../../../Psr/Cache/InvalidArgumentException.md)

***

### getList

```php
protected getList(mixed $name): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$name`   | **mixed** |             |

**Throws:**

- [`InvalidArgumentException`](../../../Psr/Cache/InvalidArgumentException.md)

***

### getTagKey

```php
protected getTagKey(string $tag): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$tag`    | **string** |             |

***

### saveTags

```php
private saveTags(\Qubus\Cache\Psr6\TaggablePsr6ItemAdapter $item): void
```

**Parameters:**

| Parameter | Type                                          | Description |
|-----------|-----------------------------------------------|-------------|
| `$item`   | **\Qubus\Cache\Psr6\TaggablePsr6ItemAdapter** |             |

**Throws:**

- [`InvalidArgumentException`](../../../Psr/Cache/InvalidArgumentException.md)

***

### invalidateTags

Invalidates cached items using tags.

```php
public invalidateTags(array $tags): bool
```

**Parameters:**

| Parameter | Type      | Description                    |
|-----------|-----------|--------------------------------|
| `$tags`   | **array** | An array of tags to invalidate |

**Return Value:**

True on success

***

### invalidateTag

Invalidates cached items using a tag.

```php
public invalidateTag(mixed $tag): bool
```

**Parameters:**

| Parameter | Type      | Description           |
|-----------|-----------|-----------------------|
| `$tag`    | **mixed** | The tag to invalidate |

**Return Value:**

True on success

***

### preRemoveItem

Removes the key form all tag lists.

```php
private preRemoveItem(string $key): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

**Throws:**

- [`InvalidArgumentException`](../../../Psr/Cache/InvalidArgumentException.md)

***

### removeTagEntries

```php
private removeTagEntries(\Qubus\Cache\Psr6\TaggableCacheItem $item): void
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$item`   | **\Qubus\Cache\Psr6\TaggableCacheItem** |             |

**Throws:**

- [`InvalidArgumentException`](../../../Psr/Cache/InvalidArgumentException.md)

***
