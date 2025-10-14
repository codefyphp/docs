***

# DateTime





* Full name: `\Qubus\ValueObjects\DateTime\DateTime`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### date



```php
protected \Qubus\ValueObjects\DateTime\Date $date
```






***

### time



```php
protected \Qubus\ValueObjects\DateTime\Time $time
```






***

## Methods


### __construct

Returns a new DateTime object.

```php
public __construct(\Qubus\ValueObjects\DateTime\Date $date, ?\Qubus\ValueObjects\DateTime\Time $time = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$date` | **\Qubus\ValueObjects\DateTime\Date** |  |
| `$time` | **?\Qubus\ValueObjects\DateTime\Time** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### __toString

Returns DateTime as string in format "Y-n-j G:i:s".

```php
public __toString(): string
```












***

### fromNative

Returns a new DateTime object from native values.

```php
public static fromNative(): \Qubus\ValueObjects\DateTime\DateTime|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

- [`InvalidDateException`](./Exception/InvalidDateException.md)



***

### fromNativeCarbonImmutable

Returns a new DateTime from native CarbonImmutable.

```php
public static fromNativeCarbonImmutable(\Carbon\CarbonImmutable $dateTime): \Qubus\ValueObjects\DateTime\DateTime
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$dateTime` | **\Carbon\CarbonImmutable** |  |




**Throws:**

- [`\Qubus\ValueObjects\DateTime\Exception\InvalidDateException|\Qubus\Exception\Data\TypeException`](./Exception/InvalidDateException|/Qubus/Exception/Data/TypeException.md)



***

### now

Returns current DateTime.

```php
public static now(): \Qubus\ValueObjects\DateTime\DateTime
```



* This method is **static**.







**Throws:**

- [`InvalidDateException`](./Exception/InvalidDateException.md)

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### equals

Tells whether two DateTime are equal by comparing their values.

```php
public equals(\Qubus\ValueObjects\ValueObject $dateTime): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$dateTime` | **\Qubus\ValueObjects\ValueObject** |  |





***

### getDate

Returns date from current DateTime.

```php
public getDate(): \Qubus\ValueObjects\DateTime\Date
```












***

### getTime

Returns time from current DateTime.

```php
public getTime(): \Qubus\ValueObjects\DateTime\Time
```












***

### toNativeCarbonImmutable

Returns a CarbonImmutable version of the current DateTime.

```php
public toNativeCarbonImmutable(): \Carbon\CarbonImmutable
```












***


***
> Automatically generated on 2025-10-13
