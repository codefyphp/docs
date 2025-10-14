***

# Dictionary





* Full name: `\Qubus\ValueObjects\Structure\Dictionary`
* Parent class: [`\Qubus\ValueObjects\Structure\Collection`](./Collection.md)




## Methods


### __construct

Returns a new Dictionary object.

```php
public __construct(\SplFixedArray $pairs): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$pairs` | **\SplFixedArray** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### fromNative

Returns a new Dictionary object.

```php
public static fromNative(): \Qubus\ValueObjects\Structure\Dictionary|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### keys

Returns a Collection of the keys.

```php
public keys(): \Qubus\ValueObjects\Structure\Collection
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### values

Returns a Collection of the values.

```php
public values(): \Qubus\ValueObjects\Structure\Collection
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### containsKey

Tells whether $object is one of the keys.

```php
public containsKey(\Qubus\ValueObjects\ValueObject $object): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$object` | **\Qubus\ValueObjects\ValueObject** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### containsValue

Tells whether $object is one of the values.

```php
public containsValue(\Qubus\ValueObjects\ValueObject $object): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$object` | **\Qubus\ValueObjects\ValueObject** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***


## Inherited methods


### __construct

Returns a new Collection object.

```php
public __construct(\SplFixedArray $items): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$items` | **\SplFixedArray** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### __toString

Returns a native string representation of the Collection object.

```php
public __toString(): string
```












***

### fromNative

Returns a new Collection object.

```php
public static fromNative(): \Qubus\ValueObjects\Structure\Collection|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### equals

Tells whether two Collection are equal by comparing their size and items (item order matters).

```php
public equals(\Qubus\ValueObjects\Structure\Collection|\Qubus\ValueObjects\ValueObject $collection): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$collection` | **\Qubus\ValueObjects\Structure\Collection&#124;\Qubus\ValueObjects\ValueObject** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### count

Returns the number of objects in the collection.

```php
public count(): \Qubus\ValueObjects\Number\Natural
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### contains

Tells whether the Collection contains an object.

```php
public contains(\Qubus\ValueObjects\ValueObject $object): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$object` | **\Qubus\ValueObjects\ValueObject** |  |





***

### toArray

Returns a native array representation of the Collection.

```php
public toArray(): array
```












***


***
> Automatically generated on 2025-10-13
