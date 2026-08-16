# ArgsParser

***

* Full name: `\Codefy\Framework\Support\ArgsParser`

## Methods

### parse

Parse and merge user arguments with defaults.

```php
public static parse(array|object|string $args, array $defaults = [], bool $deep = false): array
```

* This method is **static**.
**Parameters:**

| Parameter   | Type                      | Description                                     |
|-------------|---------------------------|-------------------------------------------------|
| `$args`     | **array\|object\|string** | Arguments passed in (array, object, or string). |
| `$defaults` | **array**                 | Default values to merge.                        |
| `$deep`     | **bool**                  | Whether to deep merge nested arrays.            |

***

### toArray

Convert object or iterable to array.

```php
protected static toArray(array|object|string $input): array
```

* This method is **static**.
**Parameters:**

| Parameter | Type                      | Description |
|-----------|---------------------------|-------------|
| `$input`  | **array\|object\|string** |             |

***

### deepMerge

Deep merge two arrays (preserving numeric keys from args).

```php
protected static deepMerge(array $defaults, array $args): array
```

* This method is **static**.
**Parameters:**

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `$defaults` | **array** |             |
| `$args`     | **array** |             |

***
