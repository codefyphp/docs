***

# Year





* Full name: `\Qubus\ValueObjects\DateTime\Year`
* Parent class: [`\Qubus\ValueObjects\Number\IntegerNumber`](../Number/IntegerNumber.md)




## Methods


### now

Returns the current year.

```php
public static now(): \Qubus\ValueObjects\DateTime\Year
```



* This method is **static**.







**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***


## Inherited methods


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

Returns a IntegerNumber object given a PHP native int as parameter.

```php
public __construct(int $value): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **int** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### toNative

Returns the value of the integer number

```php
public toNative(): float
```












***

### equals

Tells whether two IntegerNumber are equal by comparing their values

```php
public equals(\Qubus\ValueObjects\Number\IntegerNumber|\Qubus\ValueObjects\ValueObject $integer): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$integer` | **\Qubus\ValueObjects\Number\IntegerNumber&#124;\Qubus\ValueObjects\ValueObject** |  |





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

### toRealNumber

Returns a RealNumber with the value of the IntegerNumber

```php
public toRealNumber(): \Qubus\ValueObjects\Number\RealNumber
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***


***
> Automatically generated on 2025-10-13
