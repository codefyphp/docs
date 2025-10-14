***

# WeekDay





* Full name: `\Qubus\ValueObjects\DateTime\WeekDay`
* Parent class: [`\Qubus\ValueObjects\Enum\Enum`](../Enum/Enum.md)


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`MONDAY`|public| |&#039;Monday&#039;|
|`TUESDAY`|public| |&#039;Tuesday&#039;|
|`WEDNESDAY`|public| |&#039;Wednesday&#039;|
|`THURSDAY`|public| |&#039;Thursday&#039;|
|`FRIDAY`|public| |&#039;Friday&#039;|
|`SATURDAY`|public| |&#039;Saturday&#039;|
|`SUNDAY`|public| |&#039;Sunday&#039;|


## Methods


### now

Returns the current week day.

```php
public static now(): \Qubus\ValueObjects\DateTime\WeekDay
```



* This method is **static**.








***

### fromNativeCarbonImmutable

Returns a WeekDay from a PHP native \DateTime.

```php
public static fromNativeCarbonImmutable(\Carbon\CarbonImmutable $date): \Qubus\ValueObjects\DateTime\WeekDay
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$date` | **\Carbon\CarbonImmutable** |  |





***

### getNumericValue

Returns a numeric representation of the WeekDay.

```php
public getNumericValue(): int
```

1 for Monday to 7 for Sunday.










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
