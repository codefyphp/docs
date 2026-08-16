# Helper

***

* Full name: `\Qubus\Validation\Helper`

## Methods

### strIs

Determine if a given string matches a given pattern.

```php
public static strIs(string $pattern, string $value): bool
```

* This method is **static**.
**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$pattern` | **string** |             |
| `$value`   | **string** |             |

***

### arrayHas

Check if an item or items exist in an array using "dot" notation.

```php
public static arrayHas(array $array, string $key): bool
```

* This method is **static**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$array`  | **array**  |             |
| `$key`    | **string** |             |

***

### arrayGet

Get an item from an array using "dot" notation.

```php
public static arrayGet(array $array, string|null $key = null, mixed|null $default = null): mixed
```

* This method is **static**.
**Parameters:**

| Parameter  | Type             | Description |
|------------|------------------|-------------|
| `$array`   | **array**        |             |
| `$key`     | **string\|null** |             |
| `$default` | **mixed\|null**  |             |

**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)

***

### arrayDot

Flatten a multi-dimensional associative array with dots.

```php
public static arrayDot(array $array, string $prepend = ''): array
```

* This method is **static**.
**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$array`   | **array**  |             |
| `$prepend` | **string** |             |

***

### arraySet

Set an item on an array or object using dot notation.

```php
public static arraySet(mixed& $target, array|string|null $key, mixed $value, bool $overwrite = true): mixed
```

* This method is **static**.
**Parameters:**

| Parameter    | Type                    | Description |
|--------------|-------------------------|-------------|
| `$target`    | **mixed**               |             |
| `$key`       | **array\|string\|null** |             |
| `$value`     | **mixed**               |             |
| `$overwrite` | **bool**                |             |

***

### arrayUnset

Unset an item on an array or object using dot notation.

```php
public static arrayUnset(mixed& $target, array|string $key): mixed
```

* This method is **static**.
**Parameters:**

| Parameter | Type              | Description |
|-----------|-------------------|-------------|
| `$target` | **mixed**         |             |
| `$key`    | **array\|string** |             |

***

### snakeCase

Get snake_case format from given string

```php
public static snakeCase(string $value, string $delimiter = '_'): string
```

* This method is **static**.
**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$value`     | **string** |             |
| `$delimiter` | **string** |             |

***

### join

Join string[] to string with given $separator and $lastSeparator.

```php
public static join(array $pieces, string $separator, string|null $lastSeparator = null): string|int
```

* This method is **static**.
**Parameters:**

| Parameter        | Type             | Description |
|------------------|------------------|-------------|
| `$pieces`        | **array**        |             |
| `$separator`     | **string**       |             |
| `$lastSeparator` | **string\|null** |             |

***

### wraps

Wrap string[] by given $prefix and $suffix

```php
public static wraps(array $strings, string $prefix, string|null $suffix = null): array
```

* This method is **static**.
**Parameters:**

| Parameter  | Type             | Description |
|------------|------------------|-------------|
| `$strings` | **array**        |             |
| `$prefix`  | **string**       |             |
| `$suffix`  | **string\|null** |             |

***
