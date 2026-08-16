# FlatArrayTransformer

***

* Full name: `\Qubus\Support\Serializer\Transformer\FlatArrayTransformer`
* Parent class: [`\Qubus\Support\Serializer\Transformer\ArrayTransformer`](./ArrayTransformer.md)

## Methods

### serialize

```php
public serialize(mixed $value): bool|string
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### flatten

```php
private flatten(array $array, string $prefix = ''): array
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$array`  | **array**  |             |
| `$prefix` | **string** |             |

***

## Inherited methods

### recursiveUnset

```php
protected recursiveUnset(array& $array, array $unwantedKey): void
```

**Parameters:**

| Parameter      | Type      | Description |
|----------------|-----------|-------------|
| `$array`       | **array** |             |
| `$unwantedKey` | **array** |             |

***

### recursiveSetValues

```php
protected recursiveSetValues(array& $array): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$array`  | **array** |             |

***

### recursiveFlattenOneElementObjectsToScalarType

```php
protected recursiveFlattenOneElementObjectsToScalarType(array& $array, mixed|null $parentKey = null, mixed|null $currentKey = null): void
```

**Parameters:**

| Parameter     | Type            | Description |
|---------------|-----------------|-------------|
| `$array`      | **array**       |             |
| `$parentKey`  | **mixed\|null** |             |
| `$currentKey` | **mixed\|null** |             |

***

### unserialize

```php
public unserialize(mixed $value): array
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

**Throws:**

- [`TypeException`](../../../Exception/Data/TypeException.md)

***

### __construct

```php
public __construct(): mixed
```

***

### serialize

```php
public serialize(mixed $value): bool|string
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***
