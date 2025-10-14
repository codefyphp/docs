***

# Money





* Full name: `\Qubus\ValueObjects\Money\Money`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### money



```php
protected \Money\Money $money
```






***

### currency



```php
protected \Qubus\ValueObjects\Money\Currency $currency
```






***

## Methods


### fromNative

Returns a Money object from native int amount and string currency code

```php
public static fromNative(): \Qubus\ValueObjects\Money\Money|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### __construct

Returns a Money object

```php
public __construct(\Qubus\ValueObjects\Number\IntegerNumber $amount, \Qubus\ValueObjects\Money\Currency $currency): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$amount` | **\Qubus\ValueObjects\Number\IntegerNumber** | Amount expressed in the smallest units of $currency (e.g. cents) |
| `$currency` | **\Qubus\ValueObjects\Money\Currency** | Currency of the money object |





***

### equals

Tells whether two Currency are equal by comparing their amount and currency

```php
public equals(\Qubus\ValueObjects\Money\Money|\Qubus\ValueObjects\ValueObject $money): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$money` | **\Qubus\ValueObjects\Money\Money&#124;\Qubus\ValueObjects\ValueObject** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### getAmount

Returns money amount

```php
public getAmount(): \Qubus\ValueObjects\Number\IntegerNumber
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### getCurrency

Returns money currency

```php
public getCurrency(): \Qubus\ValueObjects\Money\Currency
```












***

### add

Add an integer quantity to the amount and returns a new Money object.

```php
public add(\Qubus\ValueObjects\Number\IntegerNumber $quantity): \Qubus\ValueObjects\Money\Money
```

Use a negative quantity for subtraction.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$quantity` | **\Qubus\ValueObjects\Number\IntegerNumber** | Quantity to add |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### multiply

Multiply the Money amount for a given number and returns a new Money object.

```php
public multiply(\Qubus\ValueObjects\Number\RealNumber $multiplier, mixed $roundingMode = null): \Qubus\ValueObjects\Money\Money
```

Use 0 < RealNumber $multiplier < 1 for division.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$multiplier` | **\Qubus\ValueObjects\Number\RealNumber** |  |
| `$roundingMode` | **mixed** | Rounding mode of the operation. Defaults to RoundingMode::HALF_UP. |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### __toString

Returns a string representation of the Money value in format "CUR AMOUNT" (e.g.: EUR 1000)

```php
public __toString(): string
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***


***
> Automatically generated on 2025-10-13
