***

# DateTimeWithTimeZone





* Full name: `\Qubus\ValueObjects\DateTime\DateTimeWithTimeZone`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### dateTime



```php
protected \Qubus\ValueObjects\DateTime\DateTime $dateTime
```






***

### timeZone



```php
protected \Qubus\ValueObjects\DateTime\TimeZone $timeZone
```






***

## Methods


### __construct

Returns a new DateTimeWithTimeZone object.

```php
public __construct(\Qubus\ValueObjects\DateTime\DateTime $datetime, ?\Qubus\ValueObjects\DateTime\TimeZone $timezone = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$datetime` | **\Qubus\ValueObjects\DateTime\DateTime** |  |
| `$timezone` | **?\Qubus\ValueObjects\DateTime\TimeZone** |  |





***

### __toString

Returns DateTime as string in format "Y-n-j G:i:s.u e".

```php
public __toString(): string
```












***

### fromNative

Returns a new DateTime object from native values.

```php
public static fromNative(): \Qubus\ValueObjects\DateTime\DateTimeWithTimeZone|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`\Qubus\ValueObjects\DateTime\Exception\InvalidDateException|\Qubus\ValueObjects\DateTime\Exception\InvalidTimeZoneException|\Qubus\Exception\Data\TypeException`](./Exception/InvalidDateException|/Qubus/ValueObjects/DateTime/Exception/InvalidTimeZoneException|/Qubus/Exception/Data/TypeException.md)



***

### fromNativeCarbonImmutable

Returns a new DateTime from a native PHP \DateTime.

```php
public static fromNativeCarbonImmutable(\Carbon\CarbonImmutable $nativeDatetime): \Qubus\ValueObjects\DateTime\DateTimeWithTimeZone|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$nativeDatetime` | **\Carbon\CarbonImmutable** |  |




**Throws:**

- [`InvalidDateException`](./Exception/InvalidDateException.md)

- [`InvalidTimeZoneException`](./Exception/InvalidTimeZoneException.md)

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### now

Returns a DateTimeWithTimeZone object using current DateTime and default TimeZone.

```php
public static now(): \Qubus\ValueObjects\DateTime\DateTimeWithTimeZone|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`\Qubus\ValueObjects\DateTime\Exception\InvalidTimeZoneException|\Qubus\Exception\Data\TypeException`](./Exception/InvalidTimeZoneException|/Qubus/Exception/Data/TypeException.md)

- [`InvalidDateException`](./Exception/InvalidDateException.md)



***

### equals

Tells whether two DateTimeWithTimeZone are equal by comparing their values.

```php
public equals(\Qubus\ValueObjects\DateTime\DateTimeWithTimeZone|\Qubus\ValueObjects\ValueObject $dateTimeWithTimeZone): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$dateTimeWithTimeZone` | **\Qubus\ValueObjects\DateTime\DateTimeWithTimeZone&#124;\Qubus\ValueObjects\ValueObject** |  |





***

### sameTimestampAs

Tells whether two DateTimeWithTimeZone represents the same timestamp.

```php
public sameTimestampAs(\Qubus\ValueObjects\DateTime\DateTimeWithTimeZone|\Qubus\ValueObjects\ValueObject $dateTimeWithTimeZone): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$dateTimeWithTimeZone` | **\Qubus\ValueObjects\DateTime\DateTimeWithTimeZone&#124;\Qubus\ValueObjects\ValueObject** |  |




**Throws:**

- [`Exception`](../../../Exception.md)



***

### getDateTime

Returns datetime from current DateTimeWithTimeZone.

```php
public getDateTime(): \Qubus\ValueObjects\DateTime\DateTime
```












***

### getTimeZone

Returns timezone from current DateTimeWithTimeZone.

```php
public getTimeZone(): \Qubus\ValueObjects\DateTime\TimeZone
```












***

### toNativeCarbonImmutable

Returns a Carbon version of the current DateTimeWithTimeZone.

```php
public toNativeCarbonImmutable(): \Carbon\CarbonImmutable
```











**Throws:**

- [`Exception`](../../../Exception.md)



***


***
> Automatically generated on 2025-10-13
