***

# Street





* Full name: `\Qubus\ValueObjects\Geography\Street`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### name



```php
protected \Qubus\ValueObjects\StringLiteral\StringLiteral $name
```






***

### number



```php
protected \Qubus\ValueObjects\StringLiteral\StringLiteral $number
```






***

## Methods


### __construct

Returns a new Street object.

```php
public __construct(\Qubus\ValueObjects\StringLiteral\StringLiteral $name, \Qubus\ValueObjects\StringLiteral\StringLiteral $number): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **\Qubus\ValueObjects\StringLiteral\StringLiteral** |  |
| `$number` | **\Qubus\ValueObjects\StringLiteral\StringLiteral** |  |





***

### __toString

Returns a string representation of the StringLiteral in the format defined in the constructor.

```php
public __toString(): string
```












***

### fromNative

Returns a new Street from native PHP string name and number.

```php
public static fromNative(): \Qubus\ValueObjects\Geography\Street|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

- [`BadFunctionCallException`](../../../BadFunctionCallException.md)



***

### equals

Tells whether two Street objects are equal.

```php
public equals(\Qubus\ValueObjects\Geography\Street|\Qubus\ValueObjects\ValueObject $street): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$street` | **\Qubus\ValueObjects\Geography\Street&#124;\Qubus\ValueObjects\ValueObject** |  |





***

### getName

Returns street name.

```php
public getName(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```












***

### getNumber

Returns street number.

```php
public getNumber(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```












***


***
> Automatically generated on 2025-10-13
