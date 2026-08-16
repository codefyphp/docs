# ConfigContainer

***

* Full name: `\Qubus\Config\ConfigContainer`
* Parent interfaces:
  `ValueType`

## Methods

### getConfigKey

Get an item from current configuration.

```php
public getConfigKey(string $key, mixed|null $default = null): mixed
```

**Parameters:**

| Parameter  | Type            | Description |
|------------|-----------------|-------------|
| `$key`     | **string**      |             |
| `$default` | **mixed\|null** |             |

**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)

***

### setConfigKey

Set an item in current configuration.

```php
public setConfigKey(string $key, mixed $value): void|self
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |
| `$value`  | **mixed**  |             |

***

### hasConfigKey

Checks if a key exists.

```php
public hasConfigKey(string $key): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***
