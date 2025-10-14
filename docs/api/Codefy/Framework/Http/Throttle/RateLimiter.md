***

# RateLimiter





* Full name: `\Codefy\Framework\Http\Throttle\RateLimiter`



## Properties


### conditions



```php
private \Codefy\Framework\Http\Throttle\Condition[] $conditions
```






***

### cache



```php
private \Psr\Cache\CacheItemPoolInterface $cache
```






***

## Methods


### __construct



```php
public __construct(\Psr\Cache\CacheItemPoolInterface $cache): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$cache` | **\Psr\Cache\CacheItemPoolInterface** |  |





***

### add



```php
public add(\Codefy\Framework\Http\Throttle\Condition $condition): \Codefy\Framework\Http\Throttle\RateLimiter
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$condition` | **\Codefy\Framework\Http\Throttle\Condition** |  |





***

### increment



```php
public increment(string $identifier, int $count = 1): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$identifier` | **string** |  |
| `$count` | **int** |  |




**Throws:**

- [`RateException`](./RateException.md)

- [`InvalidArgumentException`](../../../../Psr/Cache/InvalidArgumentException.md)



***

### getIntervals



```php
public getIntervals(string $identifier): \Codefy\Framework\Http\Throttle\Interval[]
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$identifier` | **string** |  |




**Throws:**

- [`InvalidArgumentException`](../../../../Psr/Cache/InvalidArgumentException.md)



***

### reset

Reset counter

```php
public reset(string $identifier): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$identifier` | **string** |  |




**Throws:**

- [`InvalidArgumentException`](../../../../Psr/Cache/InvalidArgumentException.md)



***

### getItem



```php
private getItem(string $identifier, \Codefy\Framework\Http\Throttle\Condition $condition): \Psr\Cache\CacheItemInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$identifier` | **string** |  |
| `$condition` | **\Codefy\Framework\Http\Throttle\Condition** |  |




**Throws:**

- [`InvalidArgumentException`](../../../../Psr/Cache/InvalidArgumentException.md)



***


***
> Automatically generated on 2025-10-13
