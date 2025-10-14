***

# PredisCacheAdapter





* Full name: `\Qubus\Cache\Adapter\PredisCacheAdapter`
* Parent class: [`\Qubus\Cache\Adapter\Multiple`](./Multiple.md)
* This class implements:
[`\Qubus\Cache\Adapter\CacheAdapter`](./CacheAdapter.md)



## Properties


### client



```php
private \Predis\ClientInterface $client
```






***

## Methods


### __construct



```php
public __construct(\Predis\ClientInterface $client): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$client` | **\Predis\ClientInterface** |  |





***

### get

Get a value from the cache store.

```php
public get(string $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | Cache key. |


**Return Value:**

Cache value corresponding to the key or null if no value was found.




**See Also:**

* \Qubus\Cache\Adapter\CacheAdapter::get() - 

***

### set

Sets a value into the cache store.

```php
public set(string $key, mixed $value, ?int $ttl): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | Cache key. |
| `$value` | **mixed** | Value to cache. |
| `$ttl` | **?int** | Expiration time in seconds. Null means indefinite storage time. |


**Return Value:**

True if the value has been stored successfully. False otherwise.



**Throws:**

- [`TypeException`](../TypeException.md)



**See Also:**

* \Qubus\Cache\Adapter\CacheAdapter::set() - 

***

### delete

Deletes a value from the cache store.

```php
public delete(string $key): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | Cache key. |


**Return Value:**

True if the cached value has been successfully deleted. False otherwise.




**See Also:**

* \Qubus\Cache\Adapter\CacheAdapter::delete() - 

***

### has

Checks if a value has been cached.

```php
public has(string $key): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | Cache key. |


**Return Value:**

True if the cache key corresponds to a value. False otherwise.




**See Also:**

* \Qubus\Cache\Adapter\CacheAdapter::has() - 

***

### getMultiple

Get multiple values from the cache store.

```php
public getMultiple(array $keys): iterable|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$keys` | **array** | Array of cache keys. |


**Return Value:**

Sequential array for each cache value corresponding to a key.
Null will be assigned if value was not found.




**See Also:**

* \Qubus\Cache\Adapter\CacheAdapter::getMultiple() - 

***

### setMultiple

Sets multiple values into the cache store.

```php
public setMultiple(array $values): array|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$values` | **array** | Associative array indexed by the cache key.<br />Cache value can be accessed through &quot;value&quot; key and ttl through &quot;ttl&quot; key. |


**Return Value:**

Returns null if all values have been stored successfully or an array representing all
cache keys that cannot be stored.




**See Also:**

* \Qubus\Cache\Adapter\CacheAdapter::setMultiple() - 

***

### deleteMultiple

Deletes multiple values from the cache store.

```php
public deleteMultiple(array $keys): array|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$keys` | **array** | An array of keys to delete |


**Return Value:**

A list of all keys that cannot be deleted or null if all keys has been deleted.




**See Also:**

* \Qubus\Cache\Adapter\CacheAdapter::deleteMultiple() - 

***

### purge

Purge the store of all cache values.

```php
public purge(?string $pattern): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$pattern` | **?string** | Regex pattern for targeting only certain keys or null to purge everything. |





**See Also:**

* \Qubus\Cache\Adapter\CacheAdapter::purge() - 

***

### pipeline



```php
private pipeline(\Closure $action): ?array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$action` | **\Closure** |  |





***


## Inherited methods


### getMultiple

Get multiple values from the cache store.

```php
public getMultiple(array $keys): iterable|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$keys` | **array** | Array of cache keys. |


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

| Parameter | Type | Description |
|-----------|------|-------------|
| `$values` | **array** | Associative array indexed by the cache key.<br />Cache value can be accessed through &quot;value&quot; key and ttl through &quot;ttl&quot; key. |


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

| Parameter | Type | Description |
|-----------|------|-------------|
| `$keys` | **array** | An array of keys to delete |


**Return Value:**

A list of all keys that cannot be deleted or null if all keys has been deleted.




***


***
> Automatically generated on 2025-10-13
