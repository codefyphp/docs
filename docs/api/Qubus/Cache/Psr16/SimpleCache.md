# SimpleCache

***

* Full name: `\Qubus\Cache\Psr16\SimpleCache`
* This class is marked as **final** and can't be subclassed
* This class implements:
  `CacheInterface`
* This class is a **Final class**

## Constants

| Constant     | Visibility | Type | Value     |
|--------------|------------|------|-----------|
| `CACHE_FLAG` | public     |      | "@psr16_" |

## Properties

### adapter

```php
private \Qubus\Cache\Adapter\CacheAdapter $adapter
```

***

### ttl

```php
private int|null|\DateInterval $ttl
```

***

### namespace

```php
private ?string $namespace
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Cache\Adapter\CacheAdapter $adapter, int|null|\DateInterval $ttl = null, ?string $namespace = 'default'): mixed
```

**Parameters:**

| Parameter    | Type                                  | Description |
|--------------|---------------------------------------|-------------|
| `$adapter`   | **\Qubus\Cache\Adapter\CacheAdapter** |             |
| `$ttl`       | **int\|null\|\DateInterval**          |             |
| `$namespace` | **?string**                           |             |

***

### get

{@inheritdoc}

```php
public get(string $key, mixed $default = null): mixed
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$key`     | **string** |             |
| `$default` | **mixed**  |             |

***

### set

{@inheritdoc}

```php
public set(string $key, mixed $value, null|int|\DateInterval $ttl = null): bool
```

**Parameters:**

| Parameter | Type                         | Description |
|-----------|------------------------------|-------------|
| `$key`    | **string**                   |             |
| `$value`  | **mixed**                    |             |
| `$ttl`    | **null\|int\|\DateInterval** |             |

***

### delete

{@inheritdoc}

```php
public delete(string $key): bool
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

### getMultiple

{@inheritdoc}

```php
public getMultiple(iterable $keys, mixed $default = null): iterable
```

**Parameters:**

| Parameter  | Type         | Description |
|------------|--------------|-------------|
| `$keys`    | **iterable** |             |
| `$default` | **mixed**    |             |

***

### setMultiple

{@inheritdoc}

```php
public setMultiple(iterable $values, null|int|\DateInterval $ttl = null): bool
```

**Parameters:**

| Parameter | Type                         | Description |
|-----------|------------------------------|-------------|
| `$values` | **iterable**                 |             |
| `$ttl`    | **null\|int\|\DateInterval** |             |

***

### deleteMultiple

{@inheritdoc}

```php
public deleteMultiple(iterable $keys): bool
```

**Parameters:**

| Parameter | Type         | Description |
|-----------|--------------|-------------|
| `$keys`   | **iterable** |             |

***

### has

{@inheritdoc}

```php
public has(string $key): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### getTtl

```php
private getTtl(int|null|\DateInterval $ttl): ?int
```

**Parameters:**

| Parameter | Type                         | Description |
|-----------|------------------------------|-------------|
| `$ttl`    | **int\|null\|\DateInterval** |             |

***

## Inherited methods

### reservedKeyCharacters

Reserved key characters that should not be used in a cache key.

```php
final public reservedKeyCharacters(): string
```

* This method is **final**.
***

### validateKey

Validates cache key.

```php
protected validateKey(string $key): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

**Throws:**

- [`TypeException`](../TypeException.md)

***

### isHashed

Checks if key is hashed.

```php
protected isHashed(string $key): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### prefix

Affixes a prefix to the

```php
protected prefix(string $key): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### validateKeys

Validates an array of keys.

```php
protected validateKeys(array $keys): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$keys`   | **array** |             |

**Throws:**

- [`TypeException`](../TypeException.md)

***
