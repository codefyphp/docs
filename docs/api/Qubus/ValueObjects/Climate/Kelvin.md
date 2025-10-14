***

# Kelvin





* Full name: `\Qubus\ValueObjects\Climate\Kelvin`
* Parent class: [`\Qubus\ValueObjects\Climate\Temperature`](./Temperature.md)




## Methods


### toCelsius



```php
public toCelsius(): \Qubus\ValueObjects\Climate\Celsius
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### toKelvin



```php
public toKelvin(): \Qubus\ValueObjects\Climate\Kelvin
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### toFahrenheit



```php
public toFahrenheit(): \Qubus\ValueObjects\Climate\Fahrenheit
```











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

### toCelsius



```php
public toCelsius(): \Qubus\ValueObjects\Climate\Celsius
```




* This method is **abstract**.







***

### toKelvin



```php
public toKelvin(): \Qubus\ValueObjects\Climate\Kelvin
```




* This method is **abstract**.







***

### toFahrenheit



```php
public toFahrenheit(): \Qubus\ValueObjects\Climate\Fahrenheit
```




* This method is **abstract**.







***


***
> Automatically generated on 2025-10-13
