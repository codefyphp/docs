# ArrayValueType

***

* Full name: `\Qubus\Inheritance\Contract\ArrayValueType`

## Methods

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
