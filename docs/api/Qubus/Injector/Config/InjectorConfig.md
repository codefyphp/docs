# InjectorConfig

***

* Full name: `\Qubus\Injector\Config\InjectorConfig`
* Parent class: [`ArrayObject`](../../../ArrayObject.md)
* This class implements:
  [`\Qubus\Injector\Config\Config`](./Config.md)

## Properties

### storage

```php
private array $storage
```

***

### temp

```php
private array $temp
```

***

### default

```php
private mixed $default
```

***

### delimiter

Array key level delimiter.

```php
private static string $delimiter
```

* This property is **static**.

***

## Methods

### __construct

Config constructor

```php
public __construct(array $config = [], array $default = []): mixed
```

**Parameters:**

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `$config`  | **array** |             |
| `$default` | **array** |             |

***

### all

```php
public all(): array
```

***

### get

Returns configuration value. If doesn't exist, return the set default value.

```php
public get(string $key, mixed $default = null): string|array
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$key`     | **string** |             |
| `$default` | **mixed**  |             |

***

### has

Checks if key value exists.

```php
public has(string $key): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### add

```php
public add(mixed $key, mixed $value): \Qubus\Injector\Config\InjectorConfig
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$key`    | **mixed** |             |
| `$value`  | **mixed** |             |

***

### remove

```php
public remove(mixed $withKeys): \Qubus\Injector\Config\InjectorConfig
```

**Parameters:**

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `$withKeys` | **mixed** |             |

***

### merge

```php
public merge(mixed $arrayToMerge): \Qubus\Injector\Config\InjectorConfig
```

**Parameters:**

| Parameter       | Type      | Description |
|-----------------|-----------|-------------|
| `$arrayToMerge` | **mixed** |             |

***

### toArray

```php
public toArray(): array
```

***

### toJson

```php
public toJson(): string
```

***

### __clone

```php
public __clone(): mixed
```

***

### search

```php
private static search(array $array, string|int $key, mixed $default = null): mixed
```

* This method is **static**.
**Parameters:**

| Parameter  | Type            | Description |
|------------|-----------------|-------------|
| `$array`   | **array**       |             |
| `$key`     | **string\|int** |             |
| `$default` | **mixed**       |             |

***

### count

{@inheritDoc}

```php
public count(): int
```

***

### offsetExists

{@inheritDoc}

```php
public offsetExists(mixed $index): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$index`  | **mixed** |             |

***

### offsetGet

{@inheritDoc}

```php
public offsetGet(mixed $index): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$index`  | **mixed** |             |

***

### offsetSet

{@inheritDoc}

```php
public offsetSet(mixed $index, mixed $newval): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$index`  | **mixed** |             |
| `$newval` | **mixed** |             |

***

### offsetUnset

{@inheritDoc}

```php
public offsetUnset(mixed $index): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$index`  | **mixed** |             |

***
