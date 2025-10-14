***

# ApcReflectionCache





* Full name: `\Qubus\Injector\Cache\ApcReflectionCache`
* This class implements:
[`\Qubus\Injector\Cache\ReflectionCache`](./ReflectionCache.md)



## Properties


### cache



```php
private ?\Qubus\Injector\Cache\ArrayReflectionCache $cache
```






***

### timeToLive



```php
private int $timeToLive
```






***

## Methods


### __construct

Instantiate an ApcReflectionCache object.

```php
public __construct(?\Qubus\Injector\Cache\ReflectionCache $cache = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$cache` | **?\Qubus\Injector\Cache\ReflectionCache** |  |





***

### setTimeToLive

Set the expiry time.

```php
public setTimeToLive(int $seconds): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$seconds` | **int** | The number of seconds that the cache value should live. |


**Return Value:**

Instance of the cache object.




***

### fetch

Fetch a key from the cache.

```php
public fetch(string $key): mixed|false
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | The key to fetch. |


**Return Value:**

Value of the key in the cache, or false if not found.




***

### store

Store the value for a specified key in the cache.

```php
public store(string $key, mixed $data): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | The key for which to store the value. |
| `$data` | **mixed** | The value to store under the specified key. |




**Throws:**

- [`ApcStoreException`](./ApcStoreException.md)



***


***
> Automatically generated on 2025-10-13
