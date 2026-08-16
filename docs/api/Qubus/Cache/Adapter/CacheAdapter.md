# CacheAdapter

***

* Full name: `\Qubus\Cache\Adapter\CacheAdapter`

## Methods

### get

Get a value from the cache store.

```php
public get(string $key): mixed
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** | Cache key.  |

**Return Value:**

Cache value corresponding to the key or null if no value was found.

***

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

### set

Sets a value into the cache store.

```php
public set(string $key, mixed $value, int|null $ttl): bool
```

**Parameters:**

| Parameter | Type          | Description                                                     |
|-----------|---------------|-----------------------------------------------------------------|
| `$key`    | **string**    | Cache key.                                                      |
| `$value`  | **mixed**     | Value to cache.                                                 |
| `$ttl`    | **int\|null** | Expiration time in seconds. Null means indefinite storage time. |

**Return Value:**

True if the value has been stored successfully. False otherwise.

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

### delete

Deletes a value from the cache store.

```php
public delete(string $key): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** | Cache key.  |

**Return Value:**

True if the cached value has been successfully deleted. False otherwise.

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

### has

Checks if a value has been cached.

```php
public has(string $key): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** | Cache key.  |

**Return Value:**

True if the cache key corresponds to a value. False otherwise.

***

### purge

Purge the store of all cache values.

```php
public purge(string|null $pattern): void
```

**Parameters:**

| Parameter  | Type             | Description                                                                |
|------------|------------------|----------------------------------------------------------------------------|
| `$pattern` | **string\|null** | Regex pattern for targeting only certain keys or null to purge everything. |

***
