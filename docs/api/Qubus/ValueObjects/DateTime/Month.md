***

# Month





* Full name: `\Qubus\ValueObjects\DateTime\Month`
* Parent class: [`\Qubus\ValueObjects\Enum\Enum`](../Enum/Enum.md)


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`JANUARY`|public| |&#039;January&#039;|
|`FEBRUARY`|public| |&#039;February&#039;|
|`MARCH`|public| |&#039;March&#039;|
|`APRIL`|public| |&#039;April&#039;|
|`MAY`|public| |&#039;May&#039;|
|`JUNE`|public| |&#039;June&#039;|
|`JULY`|public| |&#039;July&#039;|
|`AUGUST`|public| |&#039;August&#039;|
|`SEPTEMBER`|public| |&#039;September&#039;|
|`OCTOBER`|public| |&#039;October&#039;|
|`NOVEMBER`|public| |&#039;November&#039;|
|`DECEMBER`|public| |&#039;December&#039;|


## Methods


### now

Get current Month.

```php
public static now(): \Qubus\ValueObjects\DateTime\Month
```



* This method is **static**.








***

### fromNativeCarbonImmutable

Returns Month from a native PHP \DateTime.

```php
public static fromNativeCarbonImmutable(\Carbon\CarbonImmutable $date): \Qubus\ValueObjects\DateTime\Month
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$date` | **\Carbon\CarbonImmutable** |  |





***

### getNumericValue

Returns a numeric representation of the Month.

```php
public getNumericValue(): int
```

1 for January to 12 for December.










***


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
