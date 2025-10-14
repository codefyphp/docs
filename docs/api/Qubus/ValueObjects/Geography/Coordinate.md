***

# Coordinate





* Full name: `\Qubus\ValueObjects\Geography\Coordinate`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### latitude



```php
protected \Qubus\ValueObjects\Geography\Latitude $latitude
```






***

### longitude



```php
protected \Qubus\ValueObjects\Geography\Longitude $longitude
```






***

### ellipsoid



```php
protected ?\Qubus\ValueObjects\Geography\Ellipsoid $ellipsoid
```






***

## Methods


### __construct

Returns a new Coordinate object.

```php
public __construct(\Qubus\ValueObjects\Geography\Latitude $latitude, \Qubus\ValueObjects\Geography\Longitude $longitude, ?\Qubus\ValueObjects\Geography\Ellipsoid $ellipsoid = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$latitude` | **\Qubus\ValueObjects\Geography\Latitude** |  |
| `$longitude` | **\Qubus\ValueObjects\Geography\Longitude** |  |
| `$ellipsoid` | **?\Qubus\ValueObjects\Geography\Ellipsoid** |  |





***

### __toString

Returns a native string version of the Coordinates object in format "$latitude,$longitude".

```php
public __toString(): string
```












***

### fromNative

Returns a new Coordinate object from native PHP arguments.

```php
public static fromNative(): \Qubus\ValueObjects\Geography\Coordinate|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`BadMethodCallException`](../../../BadMethodCallException.md)



***

### equals

Tells whether tow Coordinate objects are equal.

```php
public equals(\Qubus\ValueObjects\Geography\Coordinate|\Qubus\ValueObjects\ValueObject $coordinate): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$coordinate` | **\Qubus\ValueObjects\Geography\Coordinate&#124;\Qubus\ValueObjects\ValueObject** |  |





***

### getLatitude

Returns latitude.

```php
public getLatitude(): \Qubus\ValueObjects\Geography\Latitude
```












***

### getLongitude

Returns longitude.

```php
public getLongitude(): \Qubus\ValueObjects\Geography\Longitude
```












***

### getEllipsoid

Returns ellipsoid.

```php
public getEllipsoid(): \Qubus\ValueObjects\Geography\Ellipsoid
```












***

### toDegreesMinutesSeconds

Returns a degrees/minutes/seconds representation of the coordinate.

```php
public toDegreesMinutesSeconds(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### toDecimalMinutes

Returns a decimal minutes representation of the coordinate.

```php
public toDecimalMinutes(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### toUniversalTransverseMercator

Returns a Universal Transverse Mercator projection representation of the coordinate in meters.

```php
public toUniversalTransverseMercator(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### distanceFrom

Calculates the distance between two Coordinate objects.

```php
public distanceFrom(\Qubus\ValueObjects\Geography\Coordinate $coordinate, \Qubus\ValueObjects\Geography\DistanceUnit|null $unit = null, \Qubus\ValueObjects\Geography\DistanceFormula|null $formula = null): \Qubus\ValueObjects\Number\RealNumber
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$coordinate` | **\Qubus\ValueObjects\Geography\Coordinate** |  |
| `$unit` | **\Qubus\ValueObjects\Geography\DistanceUnit&#124;null** |  |
| `$formula` | **\Qubus\ValueObjects\Geography\DistanceFormula&#124;null** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### getBaseCoordinate

Returns the underlying Coordinate object.

```php
protected static getBaseCoordinate(\Qubus\ValueObjects\Geography\Coordinate|\Qubus\ValueObjects\ValueObject $coordinate): \League\Geotools\Coordinate\Coordinate
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$coordinate` | **\Qubus\ValueObjects\Geography\Coordinate&#124;\Qubus\ValueObjects\ValueObject** |  |





***


***
> Automatically generated on 2025-10-13
