***

# RealNumber





* Full name: `\Qubus\ValueObjects\Number\RealNumber`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### value



```php
protected float $value
```






***

## Methods


### fromNative

Returns a RealNumber object given a PHP native float as parameter.

```php
public static fromNative(): \Qubus\ValueObjects\Number\RealNumber|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### __construct

Returns a RealNumber object given a PHP native float as parameter.

```php
public __construct(mixed $value): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **mixed** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### toNative

Returns the native value of the real number

```php
public toNative(): float
```












***

### equals

Tells whether two RealNumber's are equal by comparing their values.

```php
public equals(\Qubus\ValueObjects\Number\RealNumber|\Qubus\ValueObjects\ValueObject $real): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$real` | **\Qubus\ValueObjects\Number\RealNumber&#124;\Qubus\ValueObjects\ValueObject** |  |





***

### toInteger

Returns the integer part of the RealNumber number as a IntegerNumber.

```php
public toInteger(\Qubus\ValueObjects\Number\RoundingMode|null $roundingMode = null): \Qubus\ValueObjects\Number\IntegerNumber
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$roundingMode` | **\Qubus\ValueObjects\Number\RoundingMode&#124;null** | Rounding mode of the conversion.<br />Defaults to RoundingMode::HALF_UP. |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### toNatural

Returns the absolute integer part of the RealNumber number as a Natural.

```php
public toNatural(\Qubus\ValueObjects\Number\RoundingMode|null $roundingMode = null): \Qubus\ValueObjects\Number\Natural
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$roundingMode` | **\Qubus\ValueObjects\Number\RoundingMode&#124;null** | Rounding mode of the conversion.<br />Defaults to RoundingMode::HALF_UP. |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### __toString

Returns the string representation of the real value

```php
public __toString(): string
```












***


***
> Automatically generated on 2025-10-13
