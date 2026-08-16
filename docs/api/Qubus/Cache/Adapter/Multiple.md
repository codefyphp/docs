# Multiple

***

* Full name: `\Qubus\Cache\Adapter\Multiple`
* This class implements:
  [`\Qubus\Cache\Adapter\CacheAdapter`](./CacheAdapter.md)
* This class is an **Abstract class**

## Methods

### getMultiple

Get multiple values from the cache store.

```php
public getMultiple(array $keys): iterable|null
```

**Parameters:**

| Parameter | Type      | Description          |
|-----------|-----------|----------------------|
| `$keys`   | **array** | Array of cache keys. |

**Return Value:**

Sequential array for each cache value corresponding to a key.
Null will be assigned if value was not found.

***

### setMultiple

Sets multiple values into the cache store.

```php
public setMultiple(array $values): array|null
```

**Parameters:**

| Parameter | Type      | Description                                                                                                            |
|-----------|-----------|------------------------------------------------------------------------------------------------------------------------|
| `$values` | **array** | Associative array indexed by the cache key.
Cache value can be accessed through "value" key and ttl through "ttl" key. |

**Return Value:**

Returns null if all values have been stored successfully or an array representing all
cache keys that cannot be stored.

***

### deleteMultiple

Deletes multiple values from the cache store.

```php
public deleteMultiple(array $keys): array|null
```

**Parameters:**

| Parameter | Type      | Description                |
|-----------|-----------|----------------------------|
| `$keys`   | **array** | An array of keys to delete |

**Return Value:**

A list of all keys that cannot be deleted or null if all keys has been deleted.

***
