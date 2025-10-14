***

# ComplexNumber





* Full name: `\Qubus\ValueObjects\Number\ComplexNumber`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### real



```php
protected \Qubus\ValueObjects\Number\RealNumber $real
```






***

### im



```php
protected \Qubus\ValueObjects\Number\RealNumber $im
```






***

## Methods


### fromNative

Returns a new ComplexNumber object from native PHP arguments

```php
public static fromNative(): \Qubus\ValueObjects\Number\ComplexNumber|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`BadMethodCallException`](../../../BadMethodCallException.md)



***

### fromPolar

Returns a ComplexNumber given polar coordinates

```php
public static fromPolar(\Qubus\ValueObjects\Number\RealNumber $modulus, \Qubus\ValueObjects\Number\RealNumber $argument): \Qubus\ValueObjects\Number\ComplexNumber
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$modulus` | **\Qubus\ValueObjects\Number\RealNumber** |  |
| `$argument` | **\Qubus\ValueObjects\Number\RealNumber** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### __construct

Returns a ComplexNumber object give its real and imaginary parts as parameters

```php
public __construct(\Qubus\ValueObjects\Number\RealNumber $real, \Qubus\ValueObjects\Number\RealNumber $im): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$real` | **\Qubus\ValueObjects\Number\RealNumber** |  |
| `$im` | **\Qubus\ValueObjects\Number\RealNumber** |  |





***

### equals

Compare two ValueObject and tells whether they can be considered equal

```php
public equals(\Qubus\ValueObjects\Number\ComplexNumber|\Qubus\ValueObjects\ValueObject $complex): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$complex` | **\Qubus\ValueObjects\Number\ComplexNumber&#124;\Qubus\ValueObjects\ValueObject** |  |





***

### toNative

Returns the native value of the real and imaginary parts as an array

```php
public toNative(): array
```












***

### getRealNumber

Returns the real part of the complex number.

```php
public getRealNumber(): \Qubus\ValueObjects\Number\RealNumber
```












***

### getIm

Returns the imaginary part of the complex number.

```php
public getIm(): \Qubus\ValueObjects\Number\RealNumber
```












***

### getModulus

Returns the modulus (or absolute value or magnitude) of the ComplexNumber number.

```php
public getModulus(): \Qubus\ValueObjects\Number\RealNumber
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### getArgument

Returns the argument (or phase) of the ComplexNumber number.

```php
public getArgument(): \Qubus\ValueObjects\Number\RealNumber
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### __toString

Returns a native string version of the ComplexNumber object in format "${real} +|- ${complex}i"

```php
public __toString(): string
```












***


***
> Automatically generated on 2025-10-13
