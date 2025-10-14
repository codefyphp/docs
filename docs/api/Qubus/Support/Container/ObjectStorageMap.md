***

# ObjectStorageMap





* Full name: `\Qubus\Support\Container\ObjectStorageMap`
* This class implements:
[`\Psr\Container\ContainerInterface`](../../../Psr/Container/ContainerInterface.md), [`\ArrayAccess`](../../../ArrayAccess.md), [`\Countable`](../../../Countable.md), [`\IteratorAggregate`](../../../IteratorAggregate.md)



## Properties


### items



```php
private array $items
```






***

### factories



```php
private \SplObjectStorage $factories
```






***

### protected



```php
private \SplObjectStorage $protected
```






***

### frozen



```php
private array $frozen
```






***

### raw



```php
private array $raw
```






***

### keys



```php
private array $keys
```






***

## Methods


### __construct



```php
public __construct(array $items = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$items` | **array** | Pre-populate set with this key-value array |





***

### set

Set data key to value.

```php
public set(string $key, mixed $value): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | The data key |
| `$value` | **mixed** | The data value |





***

### get

Get data value with key.

```php
public get(string $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | The data key |


**Return Value:**

The data value.



**Throws:**

- [`Exception`](../../Exception/Exception.md)



***

### replace

Add data to set.

```php
public replace(array $items): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$items` | **array** | Key-value array of data to append to this set |





***

### all

Fetch set data.

```php
public all(): array
```









**Return Value:**

This set's key-value data array




***

### keys

Fetch set data keys.

```php
public keys(): array
```









**Return Value:**

This set's key-value data array keys




***

### has

Does this set contain a key?

```php
public has(string $key): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | The data key |





***

### remove

Remove value with key from this set.

```php
public remove(string $key): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | The data key |





***

### __get



```php
public __get(string $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | The data key. |




**Throws:**

- [`Exception`](../../Exception/Exception.md)



***

### __set



```php
public __set(string $key, mixed $value): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | The data key |
| `$value` | **mixed** | The data value |





***

### __isset



```php
public __isset(string $key): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | The data key |





***

### __unset



```php
public __unset(string $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | The data key |





***

### clear

Clear all items.

```php
public clear(): void
```












***

### offsetExists

Array Access

```php
public offsetExists(mixed $offset): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **mixed** |  |





***

### offsetGet



```php
public offsetGet(mixed $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### offsetSet



```php
public offsetSet(mixed $key, mixed $value): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |
| `$value` | **mixed** |  |





***

### offsetUnset



```php
public offsetUnset(mixed $key): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |





***

### count

Countable

```php
public count(): int
```












***

### getIterator

IteratorAggregate

```php
public getIterator(): \ArrayIterator
```












***

### singleton

Ensure a value or object will remain globally unique.

```php
public singleton(string $key, callable $value): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | The value or object name |
| `$value` | **callable** | The closure that defines the object |





***

### factory

Marks a callable as being a factory service.

```php
public factory(callable $callable): callable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callable` | **callable** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### protect

Protects a callable from being interpreted as a service.

```php
public protect(callable $callable): callable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callable` | **callable** | A closure to keep from being invoked and evaluated. |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### raw

Gets a parameter or the closure defining an object.

```php
public raw(string $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### extend

Extends an object definition.

```php
public extend(string $key, callable $callable): callable
```

Useful when you want to extend an existing object definition,
without necessarily loading that object.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |
| `$callable` | **callable** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### register

Registers a service provider.

```php
public register(\Qubus\Support\Container\ServiceProvider $provider, array $values = []): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$provider` | **\Qubus\Support\Container\ServiceProvider** | A ServiceProvider instance. |
| `$values` | **array** | An array of values that customizes the provider |





***


***
> Automatically generated on 2025-10-13
