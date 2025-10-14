***

# SimpleCacheStorage





* Full name: `\Qubus\Http\Session\Storage\SimpleCacheStorage`
* This class implements:
[`\Qubus\Http\Session\Storage\SessionStorage`](./SessionStorage.md)



## Properties


### cache



```php
protected \Psr\SimpleCache\CacheInterface $cache
```






***

## Methods


### __construct



```php
public __construct(\Psr\SimpleCache\CacheInterface $cache): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$cache` | **\Psr\SimpleCache\CacheInterface** |  |





***

### read

Read raw Session Data from underlying storage.

```php
public read(string $sessionId): array|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$sessionId` | **string** |  |




**Throws:**

- [`InvalidArgumentException`](../../../../Psr/SimpleCache/InvalidArgumentException.md)



***

### write

Write raw Session Data to underlying storage.

```php
public write(string $sessionId, array $data, int $ttl): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$sessionId` | **string** |  |
| `$data` | **array** |  |
| `$ttl` | **int** | time to live (in seconds) |




**Throws:**

- [`InvalidArgumentException`](../../../../Psr/SimpleCache/InvalidArgumentException.md)



***

### destroy

Destroy the entire session by forcibly removing raw Session Data from underlying storage.

```php
public destroy(string $sessionId): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$sessionId` | **string** |  |




**Throws:**

- [`InvalidArgumentException`](../../../../Psr/SimpleCache/InvalidArgumentException.md)



***


***
> Automatically generated on 2025-10-13
