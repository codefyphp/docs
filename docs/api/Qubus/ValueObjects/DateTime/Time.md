***

# Time





* Full name: `\Qubus\ValueObjects\DateTime\Time`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### hour



```php
protected \Qubus\ValueObjects\DateTime\Hour $hour
```






***

### minute



```php
protected \Qubus\ValueObjects\DateTime\Minute $minute
```






***

### second



```php
protected \Qubus\ValueObjects\DateTime\Second $second
```






***

## Methods


### __construct

Returns a new Time objects.

```php
public __construct(\Qubus\ValueObjects\DateTime\Hour $hour, \Qubus\ValueObjects\DateTime\Minute $minute, \Qubus\ValueObjects\DateTime\Second $second): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$hour` | **\Qubus\ValueObjects\DateTime\Hour** |  |
| `$minute` | **\Qubus\ValueObjects\DateTime\Minute** |  |
| `$second` | **\Qubus\ValueObjects\DateTime\Second** |  |





***

### __toString

Returns time as string in format G:i:s.

```php
public __toString(): string
```












***

### fromNative

Returns a new Time object from native int hour, minute and second.

```php
public static fromNative(): \Qubus\ValueObjects\DateTime\Time|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### fromNativeCarbonImmutable

Returns a new Time from a native CarbonImmutable.

```php
public static fromNativeCarbonImmutable(\Carbon\CarbonImmutable $time): \Qubus\ValueObjects\DateTime\Time|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **\Carbon\CarbonImmutable** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### now

Returns current Time.

```php
public static now(): \Qubus\ValueObjects\DateTime\Time|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### zero

Return zero time.

```php
public static zero(): \Qubus\ValueObjects\DateTime\Time|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### equals

Tells whether two Time are equal by comparing their values.

```php
public equals(\Qubus\ValueObjects\DateTime\Time|\Qubus\ValueObjects\ValueObject $time): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **\Qubus\ValueObjects\DateTime\Time&#124;\Qubus\ValueObjects\ValueObject** |  |





***

### getHour

Get hour.

```php
public getHour(): \Qubus\ValueObjects\DateTime\Hour
```












***

### getMinute

Get minute.

```php
public getMinute(): \Qubus\ValueObjects\DateTime\Minute
```












***

### getSecond

Get second.

```php
public getSecond(): \Qubus\ValueObjects\DateTime\Second
```












***

### toNativeCarbonImmutable

Returns a native CarbonImmutable version of the current Time.

```php
public toNativeCarbonImmutable(): \Carbon\CarbonImmutable
```

Date is set to current.










***


***
> Automatically generated on 2025-10-13
