# Serializer

***

* Full name: `\Qubus\Support\Serializer\Serializer`
* This class implements:
  [`\Qubus\Support\Serializer\Serializable`](./Serializable.md)

## Constants

| Constant               | Visibility | Type | Value     |
|------------------------|------------|------|-----------|
| `CLASS_IDENTIFIER_KEY` | public     |      | '@type'   |
| `CLASS_PARENT_KEY`     | public     |      | '@parent' |
| `SCALAR_TYPE`          | public     |      | '@scalar' |
| `SCALAR_VALUE`         | public     |      | '@value'  |
| `NULL_VAR`             | public     |      | null      |
| `MAP_TYPE`             | public     |      | '@map'    |

## Properties

### storage

Storage for object.

```php
protected \SplObjectStorage $storage
```

Used for recursion

***

### mapping

Object mapping for recursion.

```php
protected array $mapping
```

***

### mappingIndex

Object mapping index.

```php
protected int $mappingIndex
```

***

### strategy

```php
protected \Qubus\Support\Serializer\Strategy\Strategy $strategy
```

***

### dateTimeClassType

```php
private string[] $dateTimeClassType
```

***

### serializationMap

```php
protected string[] $serializationMap
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Support\Serializer\Strategy\Strategy $strategy): mixed
```

**Parameters:**

| Parameter   | Type                                            | Description |
|-------------|-------------------------------------------------|-------------|
| `$strategy` | **\Qubus\Support\Serializer\Strategy\Strategy** |             |

***

### getTransformer

This is handy specially in order to add additional data before the
serialization process takes place using the transformer public methods, if any.

```php
public getTransformer(): \Qubus\Support\Serializer\Strategy\Strategy
```

***

### serialize

Serialize the data.

```php
public serialize(mixed $data): bool|string
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **mixed** |             |

**Return Value:**

Serialized data.

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

***

### reset

Reset variables.

```php
protected reset(): void
```

***

### serializeData

Parse the data to be serialized.

```php
protected serializeData(mixed $data): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **mixed** |             |

**Throws:**

- [`SerializerException`](./SerializerException.md)
- [`ReflectionException`](../../../ReflectionException.md)

***

### isInstanceOf

Check if a class is instance or extends from the expected instance.

```php
private isInstanceOf(mixed $value, string $classFqn): bool
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$value`    | **mixed**  |             |
| `$classFqn` | **string** |             |

***

### guardForUnsupportedValues

```php
protected guardForUnsupportedValues(mixed $data): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **mixed** |             |

**Throws:**

- [`SerializerException`](./SerializerException.md)

***

### unserialize

Unserialize the value from string.

```php
public unserialize(mixed $data): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **mixed** |             |

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

***

### unserializeData

Parse the json decode to convert to objects again.

```php
protected unserializeData(mixed $data): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **mixed** |             |

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

***

### getScalarValue

```php
protected getScalarValue(mixed $value): float|bool|int|string|null
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### unserializeObject

Convert the serialized array into an object.

```php
protected unserializeObject(array $data): object|null
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **array** |             |

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

***

### unserializeDateTimeFamilyObject

```php
protected unserializeDateTimeFamilyObject(array $data, string $className): mixed
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$data`      | **array**  |             |
| `$className` | **string** |             |

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

***

### isDateTimeFamilyObject

```php
protected isDateTimeFamilyObject(string $className): bool
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$className` | **string** |             |

***

### restoreUsingUnserialize

```php
protected restoreUsingUnserialize(string $className, array $attributes): mixed
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$className`  | **string** |             |
| `$attributes` | **array**  |             |

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

***

### unserializeUserDefinedObject

```php
protected unserializeUserDefinedObject(array $data, string $className): object
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$data`      | **array**  |             |
| `$className` | **string** |             |

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

***

### setUnserializedObjectProperties

```php
protected setUnserializedObjectProperties(array $data, \ReflectionClass $ref, mixed $obj): mixed
```

**Parameters:**

| Parameter | Type                 | Description |
|-----------|----------------------|-------------|
| `$data`   | **array**            |             |
| `$ref`    | **\ReflectionClass** |             |
| `$obj`    | **mixed**            |             |

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

***

### serializeScalar

```php
protected serializeScalar(mixed $data): array|string
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **mixed** |             |

***

### serializeArray

```php
protected serializeArray(array $data): array
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **array** |             |

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

***

### serializeObject

Extract the data from an object.

```php
protected serializeObject(mixed $data): array
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **mixed** |             |

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

***

### serializeInternalClass

```php
protected serializeInternalClass(mixed $value, string $className, \ReflectionClass $ref): array
```

**Parameters:**

| Parameter    | Type                 | Description |
|--------------|----------------------|-------------|
| `$value`     | **mixed**            |             |
| `$className` | **string**           |             |
| `$ref`       | **\ReflectionClass** |             |

***

### getObjectProperties

Return the list of properties to be serialized.

```php
protected getObjectProperties(\ReflectionClass $ref, object $data): array
```

**Parameters:**

| Parameter | Type                 | Description |
|-----------|----------------------|-------------|
| `$ref`    | **\ReflectionClass** |             |
| `$data`   | **object**           |             |

***

### extractObjectData

Extract the object data.

```php
protected extractObjectData(mixed $value, \ReflectionClass $rc, array $properties): array
```

**Parameters:**

| Parameter     | Type                 | Description |
|---------------|----------------------|-------------|
| `$value`      | **mixed**            |             |
| `$rc`         | **\ReflectionClass** |             |
| `$properties` | **array**            |             |

***

### extractCurrentObjectProperties

```php
protected extractCurrentObjectProperties(mixed $value, \ReflectionClass $rc, array $properties, array& $data): void
```

**Parameters:**

| Parameter     | Type                 | Description |
|---------------|----------------------|-------------|
| `$value`      | **mixed**            |             |
| `$rc`         | **\ReflectionClass** |             |
| `$properties` | **array**            |             |
| `$data`       | **array**            |             |

***

### extractAllInhertitedProperties

```php
protected extractAllInhertitedProperties(mixed $value, \ReflectionClass $rc, array& $data): void
```

**Parameters:**

| Parameter | Type                 | Description |
|-----------|----------------------|-------------|
| `$value`  | **mixed**            |             |
| `$rc`     | **\ReflectionClass** |             |
| `$data`   | **array**            |             |

***

### isSerialized

Checks if data is serialized.

```php
private isSerialized(object|array|string $data, bool $strict = true): bool
```

**Parameters:**

| Parameter | Type                      | Description |
|-----------|---------------------------|-------------|
| `$data`   | **object\|array\|string** |             |
| `$strict` | **bool**                  |             |

***
