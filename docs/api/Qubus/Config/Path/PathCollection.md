# PathCollection

***

* Full name: `\Qubus\Config\Path\PathCollection`
* Parent class: [`\Qubus\Config\ArrayCollection`](../ArrayCollection.md)

## Methods

### add

```php
public add(mixed $value): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

**Throws:**

- [`PathNotFoundException`](./PathNotFoundException.md)

***

## Inherited methods

### __construct

```php
public __construct(array $elements = []): mixed
```

**Parameters:**

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `$elements` | **array** |             |

***

### toArray

```php
public toArray(): array
```

***

### jsonSerialize

```php
public jsonSerialize(): array
```

***

### offsetExists

```php
public offsetExists(string $offset): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$offset` | **string** |             |

***

### offsetGet

```php
public offsetGet(string $offset): mixed
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$offset` | **string** |             |

***

### offsetSet

```php
public offsetSet(mixed $offset, mixed $value): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$offset` | **mixed** |             |
| `$value`  | **mixed** |             |

***

### offsetUnset

```php
public offsetUnset(string $offset): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$offset` | **string** |             |

***

### count

```php
public count(): int
```

***

### getIterator

```php
public getIterator(): \ArrayIterator
```

***

### get

```php
public get(mixed $key, mixed|null $default = null): null|mixed
```

**Parameters:**

| Parameter  | Type            | Description |
|------------|-----------------|-------------|
| `$key`     | **mixed**       |             |
| `$default` | **mixed\|null** |             |

***

### set

```php
public set(string $key, mixed $value): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |
| `$value`  | **mixed**  |             |

***

### add

```php
public add(mixed $value): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### remove

```php
public remove(string $key): null|mixed
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### removeAll

```php
public removeAll(): void
```

***
