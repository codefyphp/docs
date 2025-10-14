***

# ArrayReflectionCache





* Full name: `\Qubus\Injector\Cache\ArrayReflectionCache`
* This class implements:
[`\Qubus\Injector\Cache\ReflectionCache`](./ReflectionCache.md)



## Properties


### cache



```php
private array $cache
```






***

## Methods


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





***


***
> Automatically generated on 2025-10-13
