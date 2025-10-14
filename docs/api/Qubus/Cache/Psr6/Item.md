***

# Item





* Full name: `\Qubus\Cache\Psr6\Item`
* This class implements:
[`\Psr\Cache\CacheItemInterface`](../../../Psr/Cache/CacheItemInterface.md)


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`EXPIRATION`|public| |&#039;now +100 years&#039;|

## Properties


### expiration



```php
protected \DateTimeInterface|\DateInterval|int|null $expiration
```






***

### key



```php
private string $key
```






***

### value



```php
private mixed $value
```






***

### isHit



```php
private bool $isHit
```






***

## Methods


### __construct



```php
public __construct(string $key, mixed $value = null, ?\DateTimeInterface $ttl = null, bool $isHit = false): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | Cache key. |
| `$value` | **mixed** | Cache value. |
| `$ttl` | **?\DateTimeInterface** |  |
| `$isHit` | **bool** |  |





***

### getKey

{@inheritdoc}

```php
public getKey(): string
```












***

### get

{@inheritdoc}

```php
public get(): mixed
```












***

### isHit

{@inheritdoc}

```php
public isHit(): bool
```












***

### set

{@inheritdoc}

```php
public set(mixed $value): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **mixed** |  |





***

### setHit

Set whether it's a cache hit or not.

```php
public setHit(bool $value): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **bool** | False or true. |





***

### expiresAt

{@inheritdoc}

```php
public expiresAt(?\DateTimeInterface $expiration): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$expiration` | **?\DateTimeInterface** |  |





***

### expiresAfter

{@inheritdoc}

```php
public expiresAfter(int|\DateInterval|null $time): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **int&#124;\DateInterval&#124;null** |  |





***

### getExpiresAt

Returns a DateInterval object.

```php
public getExpiresAt(): \DateTime|\DateInterval|\Qubus\Support\DateTime\QubusDateTimeImmutable
```












***

### getExpiresInSeconds

Returns the number of seconds a cache should expire.

```php
public getExpiresInSeconds(): int
```












***

### isExpired

Returns true if expired, false otherwise.

```php
public isExpired(): bool
```












***


***
> Automatically generated on 2025-10-13
