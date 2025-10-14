***

# KeyValuePair





* Full name: `\Qubus\ValueObjects\Structure\KeyValuePair`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### key



```php
protected \Qubus\ValueObjects\ValueObject $key
```






***

### value



```php
protected \Qubus\ValueObjects\ValueObject $value
```






***

## Methods


### __construct

Returns a KeyValuePair.

```php
public __construct(\Qubus\ValueObjects\ValueObject $key, \Qubus\ValueObjects\ValueObject $value): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **\Qubus\ValueObjects\ValueObject** |  |
| `$value` | **\Qubus\ValueObjects\ValueObject** |  |





***

### __toString

Returns a string representation of the KeyValuePair in format "$key => $value".

```php
public __toString(): string
```












***

### fromNative

Returns a KeyValuePair from native PHP arguments evaluated as strings.

```php
public static fromNative(): \Qubus\ValueObjects\Structure\KeyValuePair|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

- [`BadMethodCallException`](../../../BadMethodCallException.md)



***

### equals

Tells whether two KeyValuePair are equal.

```php
public equals(\Qubus\ValueObjects\Structure\KeyValuePair|\Qubus\ValueObjects\ValueObject $keyValuePair): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$keyValuePair` | **\Qubus\ValueObjects\Structure\KeyValuePair&#124;\Qubus\ValueObjects\ValueObject** |  |





***

### getKey

Returns key.

```php
public getKey(): \Qubus\ValueObjects\ValueObject
```












***

### getValue

Returns value.

```php
public getValue(): \Qubus\ValueObjects\ValueObject
```












***


***
> Automatically generated on 2025-10-13
