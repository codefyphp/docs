***

# TimeZone





* Full name: `\Qubus\ValueObjects\DateTime\TimeZone`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### name



```php
protected \Qubus\ValueObjects\StringLiteral\StringLiteral $name
```






***

## Methods


### __construct

Returns a new TimeZone object.

```php
public __construct(\Qubus\ValueObjects\StringLiteral\StringLiteral $name): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **\Qubus\ValueObjects\StringLiteral\StringLiteral** |  |




**Throws:**

- [`InvalidTimeZoneException`](./Exception/InvalidTimeZoneException.md)



***

### __toString

Returns timezone name as string.

```php
public __toString(): string
```












***

### fromNative

Returns a new Time object from native timezone name.

```php
public static fromNative(): \Qubus\ValueObjects\DateTime\TimeZone|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`\Qubus\ValueObjects\DateTime\Exception\InvalidTimeZoneException|\Qubus\Exception\Data\TypeException`](./Exception/InvalidTimeZoneException|/Qubus/Exception/Data/TypeException.md)



***

### fromNativeCarbonTimeZone

Returns a new Time from a native PHP \DateTime.

```php
public static fromNativeCarbonTimeZone(\Carbon\CarbonTimeZone $timezone): \Qubus\ValueObjects\DateTime\TimeZone|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$timezone` | **\Carbon\CarbonTimeZone** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

- [`InvalidTimeZoneException`](./Exception/InvalidTimeZoneException.md)



***

### fromDefault

Returns default TimeZone.

```php
public static fromDefault(): \Qubus\ValueObjects\DateTime\TimeZone|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`\Qubus\ValueObjects\DateTime\Exception\InvalidTimeZoneException|\Qubus\Exception\Data\TypeException`](./Exception/InvalidTimeZoneException|/Qubus/Exception/Data/TypeException.md)



***

### toNativeCarbonTimeZone

Returns a native CarbonTimeZone version of the current TimeZone.

```php
public toNativeCarbonTimeZone(): \Carbon\CarbonTimeZone
```











**Throws:**

- [`Exception`](../../../Exception.md)



***

### equals

Tells whether two DateTimeZone are equal by comparing their names.

```php
public equals(\Qubus\ValueObjects\ValueObject|\Qubus\ValueObjects\DateTime\TimeZone $timezone): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$timezone` | **\Qubus\ValueObjects\ValueObject&#124;\Qubus\ValueObjects\DateTime\TimeZone** |  |





***

### getName

Returns timezone name.

```php
public getName(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```












***


***
> Automatically generated on 2025-10-13
