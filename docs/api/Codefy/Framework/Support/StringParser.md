# StringParser

***

* Full name: `\Codefy\Framework\Support\StringParser`

## Methods

### parse

Parse a query string into an associative array, and merge with defaults.

```php
public static parse(string $query, array $defaults = [], bool $strict = false): array
```

* This method is **static**.
**Parameters:**

| Parameter   | Type       | Description                      |
|-------------|------------|----------------------------------|
| `$query`    | **string** | The query string to parse.       |
| `$defaults` | **array**  | An array of default values.      |
| `$strict`   | **bool**   | If true, skip malformed entries. |

***

### assignValue

Assign a value to an array, handling PHP-style array keys (e.g., foo[]=bar).

```php
protected static assignValue(array& $target, string $key, mixed $value): void
```

* This method is **static**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$target` | **array**  |             |
| `$key`    | **string** |             |
| `$value`  | **mixed**  |             |

***
