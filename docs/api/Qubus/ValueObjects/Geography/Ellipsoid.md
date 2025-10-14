***

# Ellipsoid





* Full name: `\Qubus\ValueObjects\Geography\Ellipsoid`
* Parent class: [`\Qubus\ValueObjects\Enum\Enum`](../Enum/Enum.md)


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`AIRY`|public| |&#039;AIRY&#039;|
|`AUSTRALIAN_NATIONAL`|public| |&#039;AUSTRALIAN_NATIONAL&#039;|
|`BESSEL_1841`|public| |&#039;BESSEL_1841&#039;|
|`BESSEL_1841_NAMBIA`|public| |&#039;BESSEL_1841_NAMBIA&#039;|
|`CLARKE_1866`|public| |&#039;CLARKE_1866&#039;|
|`CLARKE_1880`|public| |&#039;CLARKE_1880&#039;|
|`EVEREST`|public| |&#039;EVEREST&#039;|
|`FISCHER_1960_MERCURY`|public| |&#039;FISCHER_1960_MERCURY&#039;|
|`FISCHER_1968`|public| |&#039;FISCHER_1968&#039;|
|`GRS_1967`|public| |&#039;GRS_1967&#039;|
|`GRS_1980`|public| |&#039;GRS_1980&#039;|
|`HELMERT_1906`|public| |&#039;HELMERT_1906&#039;|
|`HOUGH`|public| |&#039;HOUGH&#039;|
|`INTERNATIONAL`|public| |&#039;INTERNATIONAL&#039;|
|`KRASSOVSKY`|public| |&#039;KRASSOVSKY&#039;|
|`MODIFIED_AIRY`|public| |&#039;MODIFIED_AIRY&#039;|
|`MODIFIED_EVEREST`|public| |&#039;MODIFIED_EVEREST&#039;|
|`MODIFIED_FISCHER_1960`|public| |&#039;MODIFIED_FISCHER_1960&#039;|
|`SOUTH_AMERICAN_1969`|public| |&#039;SOUTH_AMERICAN_1969&#039;|
|`WGS60`|public| |&#039;WGS60&#039;|
|`WGS66`|public| |&#039;WGS66&#039;|
|`WGS72`|public| |&#039;WGS72&#039;|
|`WGS84`|public| |&#039;WGS84&#039;|




## Inherited methods


### fromNative

Returns a new Enum object from passed value matching argument

```php
public static fromNative(): static
```



* This method is **static**.








***

### toNative

Returns the PHP native value of the enum

```php
public toNative(): mixed
```












***

### equals

Tells whether two Enum objects are sameValueAs by comparing their values

```php
public equals(\Qubus\ValueObjects\Enum\Enum|\Qubus\ValueObjects\ValueObject $enum): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$enum` | **\Qubus\ValueObjects\Enum\Enum&#124;\Qubus\ValueObjects\ValueObject** |  |





***

### __toString

Returns a native string representation of the Enum value

```php
public __toString(): string
```












***

### jsonSerialize



```php
public jsonSerialize(): array
```












***


***
> Automatically generated on 2025-10-13
