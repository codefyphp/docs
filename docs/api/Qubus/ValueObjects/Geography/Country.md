***

# Country





* Full name: `\Qubus\ValueObjects\Geography\Country`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### code



```php
protected \Qubus\ValueObjects\Geography\CountryCode $code
```






***

## Methods


### __construct

Returns a new Country object.

```php
public __construct(\Qubus\ValueObjects\Geography\CountryCode $code): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$code` | **\Qubus\ValueObjects\Geography\CountryCode** |  |





***

### __toString

Returns country name as native string.

```php
public __toString(): string
```












***

### fromNative

Returns a new Country object given a native PHP string country code.

```php
public static fromNative(): \Qubus\ValueObjects\Geography\Country|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.








***

### equals

Tells whether two Country are equal.

```php
public equals(\Qubus\ValueObjects\Geography\Country|\Qubus\ValueObjects\ValueObject $country): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$country` | **\Qubus\ValueObjects\Geography\Country&#124;\Qubus\ValueObjects\ValueObject** |  |





***

### getCode

Returns country code.

```php
public getCode(): \Qubus\ValueObjects\Geography\CountryCode
```












***

### getName

Returns country name.

```php
public getName(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```












***


***
> Automatically generated on 2025-10-13
