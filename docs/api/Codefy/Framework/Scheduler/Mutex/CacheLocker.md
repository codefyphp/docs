# CacheLocker

***

* Full name: `\Codefy\Framework\Scheduler\Mutex\CacheLocker`
* This class implements:
  [`\Codefy\Framework\Scheduler\Mutex\Locker`](./Locker.md)

## Properties

### cache

```php
protected \Psr\Cache\CacheItemPoolInterface $cache
```

***

## Methods

### __construct

```php
public __construct(\Psr\Cache\CacheItemPoolInterface $cache): mixed
```

**Parameters:**

| Parameter | Type                                  | Description |
|-----------|---------------------------------------|-------------|
| `$cache`  | **\Psr\Cache\CacheItemPoolInterface** |             |

***

### tryLock

```php
public tryLock(\Codefy\Framework\Scheduler\Processor\Processor $processor): bool
```

**Parameters:**

| Parameter    | Type                                                | Description |
|--------------|-----------------------------------------------------|-------------|
| `$processor` | **\Codefy\Framework\Scheduler\Processor\Processor** |             |

**Throws:**

- [`InvalidArgumentException`](../../../../Psr/Cache/InvalidArgumentException.md)

***

### hasLock

```php
public hasLock(\Codefy\Framework\Scheduler\Processor\Processor $processor): bool
```

**Parameters:**

| Parameter    | Type                                                | Description |
|--------------|-----------------------------------------------------|-------------|
| `$processor` | **\Codefy\Framework\Scheduler\Processor\Processor** |             |

**Throws:**

- [`InvalidArgumentException`](../../../../Psr/Cache/InvalidArgumentException.md)

***

### unlock

```php
public unlock(\Codefy\Framework\Scheduler\Processor\Processor $processor): bool
```

**Parameters:**

| Parameter    | Type                                                | Description |
|--------------|-----------------------------------------------------|-------------|
| `$processor` | **\Codefy\Framework\Scheduler\Processor\Processor** |             |

**Throws:**

- [`InvalidArgumentException`](../../../../Psr/Cache/InvalidArgumentException.md)

***
