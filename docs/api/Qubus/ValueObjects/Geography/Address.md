***

# Address





* Full name: `\Qubus\ValueObjects\Geography\Address`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### name



```php
protected \Qubus\ValueObjects\StringLiteral\StringLiteral $name
```






***

### street



```php
protected \Qubus\ValueObjects\Geography\Street $street
```






***

### district



```php
protected \Qubus\ValueObjects\StringLiteral\StringLiteral $district
```






***

### city



```php
protected \Qubus\ValueObjects\StringLiteral\StringLiteral $city
```






***

### region



```php
protected \Qubus\ValueObjects\StringLiteral\StringLiteral $region
```






***

### postalCode



```php
protected \Qubus\ValueObjects\StringLiteral\StringLiteral $postalCode
```






***

### country



```php
protected \Qubus\ValueObjects\Geography\Country $country
```






***

## Methods


### __construct

Returns a new Address object.

```php
public __construct(\Qubus\ValueObjects\StringLiteral\StringLiteral $name, \Qubus\ValueObjects\Geography\Street $street, \Qubus\ValueObjects\StringLiteral\StringLiteral $district, \Qubus\ValueObjects\StringLiteral\StringLiteral $city, \Qubus\ValueObjects\StringLiteral\StringLiteral $region, \Qubus\ValueObjects\StringLiteral\StringLiteral $postalCode, \Qubus\ValueObjects\Geography\Country $country): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **\Qubus\ValueObjects\StringLiteral\StringLiteral** |  |
| `$street` | **\Qubus\ValueObjects\Geography\Street** |  |
| `$district` | **\Qubus\ValueObjects\StringLiteral\StringLiteral** |  |
| `$city` | **\Qubus\ValueObjects\StringLiteral\StringLiteral** |  |
| `$region` | **\Qubus\ValueObjects\StringLiteral\StringLiteral** |  |
| `$postalCode` | **\Qubus\ValueObjects\StringLiteral\StringLiteral** |  |
| `$country` | **\Qubus\ValueObjects\Geography\Country** |  |





***

### __toString

Returns a string representation of the Address in US standard format.

```php
public __toString(): string
```












***

### fromNative

Returns a new Address from native PHP arguments.

```php
public static fromNative(): \Qubus\ValueObjects\Geography\Address|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`BadMethodCallException`](../../../BadMethodCallException.md)



***

### equals

Tells whether two Address are equal.

```php
public equals(\Qubus\ValueObjects\Geography\Address|\Qubus\ValueObjects\ValueObject $address): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$address` | **\Qubus\ValueObjects\Geography\Address&#124;\Qubus\ValueObjects\ValueObject** |  |





***

### getName

Returns addressee name.

```php
public getName(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```












***

### getStreet

Returns street.

```php
public getStreet(): \Qubus\ValueObjects\Geography\Street
```












***

### getDistrict

Returns district.

```php
public getDistrict(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```












***

### getCity

Returns city.

```php
public getCity(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```












***

### getRegion

Returns region.

```php
public getRegion(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```












***

### getPostalCode

Returns postal code.

```php
public getPostalCode(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```












***

### getCountry

Returns country.

```php
public getCountry(): \Qubus\ValueObjects\Geography\Country
```












***


***
> Automatically generated on 2025-10-13
