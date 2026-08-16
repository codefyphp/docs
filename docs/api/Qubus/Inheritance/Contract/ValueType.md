# ValueType

***

* Full name: `\Qubus\Inheritance\Contract\ValueType`
* Parent interfaces:
  [`\Qubus\Inheritance\Contract\StringValueType`](./StringValueType.md),
  [`\Qubus\Inheritance\Contract\IntValueType`](./IntValueType.md),
  [`\Qubus\Inheritance\Contract\FloatValueType`](./FloatValueType.md),
  [`\Qubus\Inheritance\Contract\BoolValueType`](./BoolValueType.md),
  [`\Qubus\Inheritance\Contract\ArrayValueType`](./ArrayValueType.md)

## Inherited methods

### array

Get the specified array value.

```php
public array(string $key, callable|array<array-key,mixed>|null $default = null): array
```

**Parameters:**

| Parameter  | Type                                       | Description |
|------------|--------------------------------------------|-------------|
| `$key`     | **string**                                 |             |
| `$default` | **callable\|array<array-key,mixed>\|null** |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***

### boolean

Get the specified boolean value.

```php
public boolean(string $key, callable|bool|null $default = null): bool
```

**Parameters:**

| Parameter  | Type                     | Description |
|------------|--------------------------|-------------|
| `$key`     | **string**               |             |
| `$default` | **callable\|bool\|null** |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***

### float

Get the specified float value.

```php
public float(string $key, callable|float|null $default = null): float
```

**Parameters:**

| Parameter  | Type                      | Description |
|------------|---------------------------|-------------|
| `$key`     | **string**                |             |
| `$default` | **callable\|float\|null** |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***

### integer

Get the specified integer value.

```php
public integer(string $key, callable|int|null $default = null): int
```

**Parameters:**

| Parameter  | Type                    | Description |
|------------|-------------------------|-------------|
| `$key`     | **string**              |             |
| `$default` | **callable\|int\|null** |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***

### string

Get the specified string value.

```php
public string(string $key, callable|string|null $default = null): string
```

**Parameters:**

| Parameter  | Type                       | Description |
|------------|----------------------------|-------------|
| `$key`     | **string**                 |             |
| `$default` | **callable\|string\|null** |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***
