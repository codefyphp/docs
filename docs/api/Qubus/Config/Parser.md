# Parser

***

* Full name: `\Qubus\Config\Parser`

## Methods

### getKey

```php
public static getKey(string $name): array
```

* This method is **static**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### getValue

```php
public static getValue(array|null $haystack = null, string|null $key = null, null|array $sub = null, mixed|null $default = null): mixed
```

* This method is **static**.
**Parameters:**

| Parameter   | Type             | Description |
|-------------|------------------|-------------|
| `$haystack` | **array\|null**  |             |
| `$key`      | **string\|null** |             |
| `$sub`      | **null\|array**  |             |
| `$default`  | **mixed\|null**  |             |

***

### findInMultiArray

```php
private static findInMultiArray(array $needle, array $haystack): mixed
```

* This method is **static**.
**Parameters:**

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `$needle`   | **array** |             |
| `$haystack` | **array** |             |

***
