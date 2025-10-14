***

# Currency





* Full name: `\Qubus\ValueObjects\Money\Currency`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### currency



```php
protected \Money\Currency $currency
```






***

### code



```php
protected \Qubus\ValueObjects\Money\CurrencyCode $code
```






***

## Methods


### fromNative

Returns a new Currency object from native string currency code

```php
public static fromNative(): \Qubus\ValueObjects\Money\Currency|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.








***

### __construct



```php
public __construct(\Qubus\ValueObjects\Money\CurrencyCode $code): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$code` | **\Qubus\ValueObjects\Money\CurrencyCode** |  |





***

### equals

Tells whether two Currency are equal by comparing their names

```php
public equals(\Qubus\ValueObjects\Money\Currency|\Qubus\ValueObjects\ValueObject $currency): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$currency` | **\Qubus\ValueObjects\Money\Currency&#124;\Qubus\ValueObjects\ValueObject** |  |





***

### getCode

Returns currency code

```php
public getCode(): \Qubus\ValueObjects\Money\CurrencyCode
```












***

### __toString

Returns string representation of the currency

```php
public __toString(): string
```












***


***
> Automatically generated on 2025-10-13
