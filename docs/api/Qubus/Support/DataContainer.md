***

# DataContainer





* Full name: `\Qubus\Support\DataContainer`
* This class implements:
[`\ArrayAccess`](../../ArrayAccess.md), [`\IteratorAggregate`](../../IteratorAggregate.md), [`\Countable`](../../Countable.md)



## Properties


### parent



```php
protected ?\Qubus\Support\DataContainer $parent
```






***

### parentEnabled



```php
protected bool $parentEnabled
```






***

### data



```php
protected array $data
```






***

### readOnly



```php
protected bool $readOnly
```






***

### isModified



```php
public bool $isModified
```






***

### dataType



```php
public \Qubus\Support\DataObjectCollection $dataType
```






***

## Methods


### __construct

Constructor

```php
public __construct(\Qubus\Support\DataObjectCollection $dataType, array $data = [], bool $readOnly = false): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$dataType` | **\Qubus\Support\DataObjectCollection** | String or Array data type. |
| `$data` | **array** | Container data. |
| `$readOnly` | **bool** | Whether the container is read-only. |





***

### getParent

Get the parent of this container.

```php
public getParent(): \Qubus\Support\DataContainer
```












***

### setParent

Set the parent of this container, to support inheritance.

```php
public setParent(\Qubus\Support\DataContainer|null $parent = null): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$parent` | **\Qubus\Support\DataContainer&#124;null** | the parent container object |





***

### enableParent

Enable the use of the parent object, if set.

```php
public enableParent(): $this
```












***

### disableParent

Disable the use of the parent object.

```php
public disableParent(): $this
```












***

### hasParent

Check whether this container has an active parent.

```php
public hasParent(): bool
```












***

### setContents

Replace the container's data.

```php
public setContents(array $data): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** | new data |




**Throws:**

- [`RuntimeException`](../../RuntimeException.md)



***

### getContents

Get the container's data.

```php
public getContents(): array
```









**Return Value:**

container's data



**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### setReadOnly

Set whether the container is read-only.

```php
public setReadOnly(bool $readOnly = true): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$readOnly` | **bool** | whether it&#039;s a read-only container |





***

### merge

Merge arrays into the container.

```php
public merge(array $arg): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$arg` | **array** | array to merge with |




**Throws:**

- [`\RuntimeException|\Qubus\Exception\Data\TypeException`](../../RuntimeException|/Qubus/Exception/Data/TypeException.md)



***

### isReadOnly

Check whether the container is read-only.

```php
public isReadOnly(): bool
```









**Return Value:**

$readOnly  whether it's a read-only container




***

### __isset

isset magic method

```php
public __isset(mixed $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### has

Check if a key was set upon this bag's data

```php
public has(string $key): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### __get

get magic method

```php
public __get(mixed $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### get

Get a key's value from the container.

```php
public get(?string $key = null, mixed $default = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **?string** |  |
| `$default` | **mixed** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### __set

set magic method

```php
public __set(mixed $key, mixed $value): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |
| `$value` | **mixed** |  |





***

### set

Set a config value.

```php
public set(?string $key, mixed $value): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **?string** |  |
| `$value` | **mixed** |  |




**Throws:**

- [`RuntimeException`](../../RuntimeException.md)



***

### delete

Delete data from the container.

```php
public delete(string $key): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | key to delete. |


**Return Value:**

delete success bool




***

### offsetExists

Allow usage of isset() on the param bag as an array.

```php
public offsetExists(string $offset): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **string** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### offsetGet

Allow fetching values as an array.

```php
public offsetGet(string $offset): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **string** |  |




**Throws:**

- [`OutOfBoundsException`](../../OutOfBoundsException.md)

- [`TypeException`](../Exception/Data/TypeException.md)



***

### offsetSet

Disallow setting values like an array.

```php
public offsetSet(string $offset, mixed $value): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **string** |  |
| `$value` | **mixed** |  |





***

### offsetUnset

Disallow unsetting values like an array.

```php
public offsetUnset(string $offset): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **string** |  |




**Throws:**

- [`RuntimeException`](../../RuntimeException.md)



***

### getIterator

IteratorAggregate implementation.

```php
public getIterator(): \ArrayIterator
```









**Return Value:**

iterator



**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### count

Countable implementation.

```php
public count(): int
```









**Return Value:**

number of items stored in the container



**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### result

Checks if a return value is a Closure without params, and if
so executes it before returning it.

```php
public result(mixed $val): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$val` | **mixed** |  |


**Return Value:**

closure result




***


***
> Automatically generated on 2025-10-13
