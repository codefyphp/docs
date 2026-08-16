# DataValidator

***

* Full name: `\Codefy\Framework\Validation\DataValidator`

## Methods

### all

Return all input data as an array.

```php
public all(): array
```

***

### only

Replace internal data with only the specified keys.

```php
public only(string[] $keys): static
```

**Parameters:**

| Parameter | Type         | Description |
|-----------|--------------|-------------|
| `$keys`   | **string[]** |             |

***

### except

Replace internal data excluding the specified keys.

```php
public except(string[] $keys): static
```

**Parameters:**

| Parameter | Type         | Description |
|-----------|--------------|-------------|
| `$keys`   | **string[]** |             |

***

### validated

Validate the request data and return validated data.

```php
public validated(): array
```

**Throws:**

- [`Exception`](../../../Exception.md)

***

### value

Return validated or filtered value.

```php
public value(mixed $value, mixed|null $default = null): mixed
```

**Parameters:**

| Parameter  | Type            | Description |
|------------|-----------------|-------------|
| `$value`   | **mixed**       |             |
| `$default` | **mixed\|null** |             |

**Throws:**

- [`Exception`](../../../Exception.md)

***

### errors

Return validation errors.

```php
public errors(): \Qubus\Validation\ErrorBag
```

***
