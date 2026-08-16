# ArrayCollection

Borrowed from ramsey/collection

***

* Full name: `\Qubus\Support\Collection\ArrayCollection`
* Parent class: [`\Qubus\Support\Collection\Collection`](./Collection.md)
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Properties

### items

The items of this array.

```php
protected array $items
```

***

## Methods

### __construct

Constructs a new array object.

```php
public __construct(array $items): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$items`  | **array** |             |

***

### type

Collection type.

```php
protected type(): string
```

***

## Inherited methods

### __construct

Constructs a new array object.

```php
public __construct(array $items): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$items`  | **array** |             |

***

### getIterator

Returns array as iterator.

```php
public getIterator(): \ArrayIterator<array>
```

***

### offsetExists

Returns `true` if the given offset exists in the array.

```php
public offsetExists(mixed $offset): bool
```

**Parameters:**

| Parameter | Type      | Description          |
|-----------|-----------|----------------------|
| `$offset` | **mixed** | The offset to check. |

***

### offsetGet

Returns the value at the specified offset.

```php
public offsetGet(mixed $offset): mixed
```

**Parameters:**

| Parameter | Type      | Description                                      |
|-----------|-----------|--------------------------------------------------|
| `$offset` | **mixed** | The offset for which a value should be returned. |

**Return Value:**

The value stored at the offset, or null if the offset
does not exist.

***

### offsetSet

Sets the given value to the given offset in the array.

```php
public offsetSet(mixed $offset, mixed $value): void
```

**Parameters:**

| Parameter | Type      | Description                           |
|-----------|-----------|---------------------------------------|
| `$offset` | **mixed** | The offset to set.                    |
| `$value`  | **mixed** | The value to set at the given offset. |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***

### offsetUnset

Removes the given offset and its value from the array.

```php
public offsetUnset(mixed $offset): void
```

**Parameters:**

| Parameter | Type      | Description                          |
|-----------|-----------|--------------------------------------|
| `$offset` | **mixed** | The offset to remove from the array. |

***

### serialize

Returns a JSON string.

```php
public serialize(): string
```

***

### unserialize

Converts a serialized string representation into an instance object.

```php
public unserialize(array $items): void
```

**Parameters:**

| Parameter | Type      | Description                 |
|-----------|-----------|-----------------------------|
| `$items`  | **array** | A PHP array to unserialize. |

***

### count

Total number of collections.

```php
public count(): int
```

***

### clear

Removes all items from array instance.

```php
public clear(): void
```

***

### toArray

Returns an instance as an array.

```php
public toArray(): array
```

***

### isEmpty

Returns `true` if array is empty.

```php
public isEmpty(): bool
```

***

### items

Returns an array of collections.

```php
public items(): array
```

***

### extractValue

Extracts the value of the given property or method from the object.

```php
protected extractValue(mixed $object, string|null $propertyOrMethod = null): mixed
```

**Parameters:**

| Parameter           | Type             | Description                                                     |
|---------------------|------------------|-----------------------------------------------------------------|
| `$object`           | **mixed**        | The object to extract the value from.                           |
| `$propertyOrMethod` | **string\|null** | The property or method for which the
value should be extracted. |

**Return Value:**

the value extracted from the specified property or method.

**Throws:**

if the method or property is not defined.
- [`ValueExtractionException`](./ValueExtractionException.md)

***

### toolValueToString

Returns a string representation of the value.

```php
protected toolValueToString(mixed $value = null): string
```

- null value: `'NULL'`
- boolean: `'TRUE'`, `'FALSE'`
- array: `'Array'`
- scalar: converted-value
- resource: `'(type resource #number)'`
- object with `__toString()`: result of `__toString()`
- object DateTime: ISO 8601 date
- object: `'(className Object)'`
- anonymous function: same as object

**Parameters:**

| Parameter | Type      | Description                      |
|-----------|-----------|----------------------------------|
| `$value`  | **mixed** | the value to return as a string. |

***

### checkType

Returns true if value is of specified type.

```php
protected checkType(string $type, mixed $value): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$type`   | **string** |             |
| `$value`  | **mixed**  |             |

***

### add

Add an item to the collection.

```php
public add(mixed $item): self<string, array>
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$item`   | **mixed** |             |

***

### getType

Returns the type of the collection.

```php
public getType(): string
```

***

### contains

Returns `true` if this collection contains the specified element.

```php
public contains(mixed $element, bool $strict = true): bool
```

**Parameters:**

| Parameter  | Type      | Description                                           |
|------------|-----------|-------------------------------------------------------|
| `$element` | **mixed** | The element to check whether the collection contains. |
| `$strict`  | **bool**  | Whether to perform a strict type check on the value.  |

***

### map

Returns a new instance of the collection with the callback function
$callable applied to each item

```php
public map(callable $callable): self<string, array>
```

**Parameters:**

| Parameter   | Type         | Description |
|-------------|--------------|-------------|
| `$callable` | **callable** |             |

***

### mapWithKeys

Run an associative map over each of the items.

```php
public mapWithKeys(callable $callback): self<string, array>
```

The callback should return an associative array with a single key/value pair.

**Parameters:**

| Parameter   | Type         | Description |
|-------------|--------------|-------------|
| `$callback` | **callable** |             |

***

### each

Applies the callback function $callable to each item in the collection.

```php
public each(callable $callable): self<string, array>
```

**Parameters:**

| Parameter   | Type         | Description |
|-------------|--------------|-------------|
| `$callable` | **callable** |             |

***

### flip

Flip the items in the collection.

```php
public flip(): self<string, array>
```

***

### filter

Filter the collection items through the callable.

```php
public filter(callable|null $callable = null): self<string, array>
```

**Parameters:**

| Parameter   | Type               | Description |
|-------------|--------------------|-------------|
| `$callable` | **callable\|null** | $callable   |

***

### get

Get the specified item from the collection.

```php
public get(mixed $key): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$key`    | **mixed** |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***

### slice

Slice the underlying collection array.

```php
public slice(int $offset, int|null $length = null): self<string, array>
```

**Parameters:**

| Parameter | Type          | Description |
|-----------|---------------|-------------|
| `$offset` | **int**       |             |
| `$length` | **int\|null** |             |

***

### nth

Create a new collection consisting of every n-th element.

```php
public nth(int $step, int $offset = 0): self<string, array>
```

**Parameters:**

| Parameter | Type    | Description |
|-----------|---------|-------------|
| `$step`   | **int** |             |
| `$offset` | **int** |             |

***

### reject

Reject the collection items through the callable.

```php
public reject(callable $callable): self<string, array>
```

**Parameters:**

| Parameter   | Type         | Description |
|-------------|--------------|-------------|
| `$callable` | **callable** |             |

***

### push

Push an item to the collection.

```php
public push(mixed $value): self<string, array>
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### put

Put the specified item in the collection with the given key.

```php
public put(mixed $key, mixed $value): self<string, array>
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$key`    | **mixed** |             |
| `$value`  | **mixed** |             |

***

### values

Returns a new Collection instance containing an
indexed array of values.

```php
public values(): self<string, array>
```

***

### flatten

Returns a new Collection instance containing a
flattened array of items.

```php
public flatten(): self<string, array>
```

***

### sort

Sort the collection of item values through a user-defined
comparison function.

```php
public sort(callable|null $callback = null): self<string, array>
```

**Parameters:**

| Parameter   | Type               | Description |
|-------------|--------------------|-------------|
| `$callback` | **callable\|null** |             |

***

### sortByKey

Sort the collection of item keys through a user-defined
comparison function.

```php
public sortByKey(callable|null $callback = null): self<string, array>
```

**Parameters:**

| Parameter   | Type               | Description |
|-------------|--------------------|-------------|
| `$callback` | **callable\|null** |             |

***

### reverse

Reverse the collection items.

```php
public reverse(): self<string, array>
```

***

### search

Search the collection for a given value and return the corresponding key if successful.

```php
public search(mixed $value, bool $strict = false): string|int|bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |
| `$strict` | **bool**  |             |

***

### groupBy

Group an associative array by a field or using a callback.

```php
public groupBy(callable $callback): self<string, array>
```

**Parameters:**

| Parameter   | Type         | Description |
|-------------|--------------|-------------|
| `$callback` | **callable** |             |

***

### keys

Returns a new Collection instance containing an
indexed array of keys.

```php
public keys(): self<string, array>
```

***

### all

Returns all items in collection.

```php
public all(): array
```

***

### pop

Get and remove the last item from the collection.

```php
public pop(): mixed|null
```

***

### last

Get the last item from the collection.

```php
public last(): mixed|null
```

***

### shift

Get and remove the first item from the collection.

```php
public shift(): mixed|null
```

***

### first

Get the first item from the collection.

```php
public first(): mixed|null
```

***

### sum

Get the sum of the collection items.

```php
public sum(mixed|null $callback = null): int|float
```

**Parameters:**

| Parameter   | Type            | Description |
|-------------|-----------------|-------------|
| `$callback` | **mixed\|null** |             |

***

### merge

Merge items with current collection.

```php
public merge(array $items): self<string, array>
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$items`  | **array** |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***

### column

Returns the values from the given property or method.

```php
public column(string $propertyOrMethod): array
```

**Parameters:**

| Parameter           | Type       | Description                               |
|---------------------|------------|-------------------------------------------|
| `$propertyOrMethod` | **string** | The property or method name to filter by. |

**Throws:**

- [`ValueExtractionException`](./ValueExtractionException.md)

***

### replace

Replace the collection items with the given items.

```php
public replace(array $items): self<string, array>
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$items`  | **array** |             |

***

### replaceRecursive

Recursively replace the collection items with the given items.

```php
public replaceRecursive(array $items): self<string, array>
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$items`  | **array** |             |

***

### only

Return a new array containing only the specified keys.

```php
public only(array $keys): self<string, array>
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$keys`   | **array** |             |

***

### except

Return a new array excluding the specified keys.

```php
public except(array $keys): self<string, array>
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$keys`   | **array** |             |

***

### type

Collection type.

```php
protected type(): string
```

* This method is **abstract**.
***
