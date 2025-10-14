***

# Date





* Full name: `\Qubus\ValueObjects\DateTime\Date`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### year



```php
public \Qubus\ValueObjects\DateTime\Year $year
```






***

### month



```php
public \Qubus\ValueObjects\DateTime\Month $month
```






***

### day



```php
public \Qubus\ValueObjects\DateTime\MonthDay $day
```






***

## Methods


### __construct

Create a new Date.

```php
public __construct(\Qubus\ValueObjects\DateTime\Year $year, \Qubus\ValueObjects\DateTime\Month $month, \Qubus\ValueObjects\DateTime\MonthDay $day): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$year` | **\Qubus\ValueObjects\DateTime\Year** |  |
| `$month` | **\Qubus\ValueObjects\DateTime\Month** |  |
| `$day` | **\Qubus\ValueObjects\DateTime\MonthDay** |  |




**Throws:**

- [`InvalidDateException`](./Exception/InvalidDateException.md)



***

### __toString

Returns date as string in format Y-n-j.

```php
public __toString(): string
```












***

### fromNative

Returns a new Date from native year, month and day values.

```php
public static fromNative(): \Qubus\ValueObjects\DateTime\Date|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

- [`InvalidDateException`](./Exception/InvalidDateException.md)



***

### fromNativeCarbonImmutable

Returns a new Date from CarbonImmutable.

```php
public static fromNativeCarbonImmutable(\Carbon\CarbonImmutable $date): \Qubus\ValueObjects\DateTime\Date
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$date` | **\Carbon\CarbonImmutable** |  |




**Throws:**

- [`\Qubus\ValueObjects\DateTime\Exception\InvalidDateException|\Qubus\Exception\Data\TypeException`](./Exception/InvalidDateException|/Qubus/Exception/Data/TypeException.md)



***

### now

Returns current Date.

```php
public static now(): \Qubus\ValueObjects\DateTime\Date
```



* This method is **static**.







**Throws:**

- [`InvalidDateException`](./Exception/InvalidDateException.md)

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### equals

Tells whether two Date are equal by comparing their values.

```php
public equals(\Qubus\ValueObjects\ValueObject|\Qubus\ValueObjects\DateTime\Date $date): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$date` | **\Qubus\ValueObjects\ValueObject&#124;\Qubus\ValueObjects\DateTime\Date** |  |





***

### getYear

Get year.

```php
public getYear(): \Qubus\ValueObjects\DateTime\Year
```












***

### getMonth

Get month.

```php
public getMonth(): \Qubus\ValueObjects\DateTime\Month
```












***

### getDay

Get day.

```php
public getDay(): \Qubus\ValueObjects\DateTime\MonthDay
```












***

### toNativeCarbonImmutable

Returns a CarbonImmutable version of the current Date.

```php
public toNativeCarbonImmutable(): \Carbon\CarbonImmutable
```












***


***
> Automatically generated on 2025-10-13
