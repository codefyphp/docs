# VariableDecorator

***

* Full name: `\Qubus\Config\VariableDecorator`
* This class implements:
  [`\Qubus\Config\ConfigContainer`](./ConfigContainer.md)

## Properties

### config

```php
public \Qubus\Config\ConfigContainer $config
```

***

### variables

```php
private array $variables
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Config\ConfigContainer $configContainer): mixed
```

**Parameters:**

| Parameter          | Type                              | Description |
|--------------------|-----------------------------------|-------------|
| `$configContainer` | **\Qubus\Config\ConfigContainer** |             |

***

### setVariables

```php
public setVariables(array $map): self
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$map`    | **array** |             |

***

### getConfigKey

Get an item from current configuration.

```php
public getConfigKey(string $key, mixed $default = null): mixed
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$key`     | **string** |             |
| `$default` | **mixed**  |             |

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

### string

```php
public string(string $key, mixed $default = null): string
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$key`     | **string** |             |
| `$default` | **mixed**  |             |

***

### integer

```php
public integer(string $key, mixed $default = null): int
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$key`     | **string** |             |
| `$default` | **mixed**  |             |

***

### float

```php
public float(string $key, mixed $default = null): float
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$key`     | **string** |             |
| `$default` | **mixed**  |             |

***

### boolean

```php
public boolean(string $key, mixed $default = null): bool
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$key`     | **string** |             |
| `$default` | **mixed**  |             |

***

### array

```php
public array(string $key, mixed $default = null): array
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$key`     | **string** |             |
| `$default` | **mixed**  |             |

***

### replaceVariables

```php
private replaceVariables(mixed $value): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***
