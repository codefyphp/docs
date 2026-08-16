# ConfigValue

***

* Full name: `\Qubus\FileSystem\ConfigValue`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Methods

### string

```php
public static string(\Qubus\Config\ConfigContainer $config, string $key, mixed|null $default = null): string
```

* This method is **static**.
**Parameters:**

| Parameter  | Type                              | Description |
|------------|-----------------------------------|-------------|
| `$config`  | **\Qubus\Config\ConfigContainer** |             |
| `$key`     | **string**                        |             |
| `$default` | **mixed\|null**                   |             |

**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)
- [`Exception`](../Exception/Exception.md)

***

### integer

```php
public static integer(\Qubus\Config\ConfigContainer $config, string $key, int $default): int
```

* This method is **static**.
**Parameters:**

| Parameter  | Type                              | Description |
|------------|-----------------------------------|-------------|
| `$config`  | **\Qubus\Config\ConfigContainer** |             |
| `$key`     | **string**                        |             |
| `$default` | **int**                           |             |

**Throws:**

- [`Exception`](../Exception/Exception.md)
- [`TypeException`](../Exception/Data/TypeException.md)

***

### boolean

```php
public static boolean(\Qubus\Config\ConfigContainer $config, string $key, bool $default): bool
```

* This method is **static**.
**Parameters:**

| Parameter  | Type                              | Description |
|------------|-----------------------------------|-------------|
| `$config`  | **\Qubus\Config\ConfigContainer** |             |
| `$key`     | **string**                        |             |
| `$default` | **bool**                          |             |

**Throws:**

- [`Exception`](../Exception/Exception.md)
- [`TypeException`](../Exception/Data/TypeException.md)

***

### nullableString

```php
public static nullableString(\Qubus\Config\ConfigContainer $config, string $key, string|null $default = null): string|null
```

* This method is **static**.
**Parameters:**

| Parameter  | Type                              | Description |
|------------|-----------------------------------|-------------|
| `$config`  | **\Qubus\Config\ConfigContainer** |             |
| `$key`     | **string**                        |             |
| `$default` | **string\|null**                  |             |

**Throws:**

- [`Exception`](../Exception/Exception.md)
- [`TypeException`](../Exception/Data/TypeException.md)

***

### nullableBoolean

```php
public static nullableBoolean(\Qubus\Config\ConfigContainer $config, string $key): bool|null
```

* This method is **static**.
**Parameters:**

| Parameter | Type                              | Description |
|-----------|-----------------------------------|-------------|
| `$config` | **\Qubus\Config\ConfigContainer** |             |
| `$key`    | **string**                        |             |

**Throws:**

- [`Exception`](../Exception/Exception.md)
- [`TypeException`](../Exception/Data/TypeException.md)

***

### nullableStringList

```php
public static nullableStringList(\Qubus\Config\ConfigContainer $config, string $key): string|list<string>|null
```

* This method is **static**.
**Parameters:**

| Parameter | Type                              | Description |
|-----------|-----------------------------------|-------------|
| `$config` | **\Qubus\Config\ConfigContainer** |             |
| `$key`    | **string**                        |             |

**Throws:**

- [`Exception`](../Exception/Exception.md)
- [`TypeException`](../Exception/Data/TypeException.md)

***

### invalidType

```php
private static invalidType(string $key, string $expected, mixed $value): \Qubus\Exception\Data\TypeException
```

* This method is **static**.
**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$key`      | **string** |             |
| `$expected` | **string** |             |
| `$value`    | **mixed**  |             |

**Throws:**

- [`Exception`](../Exception/Exception.md)

***
