***

# Collection





* Full name: `\Qubus\ValueObjects\Structure\Collection`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### items



```php
protected \SplFixedArray $items
```






***

## Methods


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
