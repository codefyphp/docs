***

# BaseArray

Borrowed from ramsey/collection



* Full name: `\Qubus\Support\Collection\BaseArray`
* This class implements:
[`\Qubus\Support\Collection\Arrayable`](./Arrayable.md)
* This class is an **Abstract class**



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
public __construct(array $items = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$items` | **array** | The initial items to add to array. |





***

### getIterator

Returns array as iterator.

```php
public getIterator(): \Traversable
```












***

### offsetExists

Returns `true` if the given offset exists in the array.

```php
public offsetExists(mixed $offset): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **mixed** | The offset to check. |





***

### offsetGet

Returns the value at the specified offset.

```php
public offsetGet(mixed $offset): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
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

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **mixed** | The offset to set. |
| `$value` | **mixed** | The value to set at the given offset. |





***

### offsetUnset

Removes the given offset and its value from the array.

```php
public offsetUnset(mixed $offset): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
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

| Parameter | Type | Description |
|-----------|------|-------------|
| `$items` | **array** | A PHP array to unserialize. |





***

### count

Returns the number of items in the array.

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


***
> Automatically generated on 2025-10-13
