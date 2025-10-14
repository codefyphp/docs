***

# Name





* Full name: `\Qubus\ValueObjects\Person\Name`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### firstName



```php
protected \Qubus\ValueObjects\StringLiteral\StringLiteral $firstName
```






***

### middleName



```php
protected \Qubus\ValueObjects\StringLiteral\StringLiteral $middleName
```






***

### lastName



```php
protected \Qubus\ValueObjects\StringLiteral\StringLiteral $lastName
```






***

## Methods


### __construct

Returns a Name object.

```php
public __construct(\Qubus\ValueObjects\StringLiteral\StringLiteral $firstName, \Qubus\ValueObjects\StringLiteral\StringLiteral $middleName, \Qubus\ValueObjects\StringLiteral\StringLiteral $lastName): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$firstName` | **\Qubus\ValueObjects\StringLiteral\StringLiteral** |  |
| `$middleName` | **\Qubus\ValueObjects\StringLiteral\StringLiteral** |  |
| `$lastName` | **\Qubus\ValueObjects\StringLiteral\StringLiteral** |  |





***

### __toString

Returns the full name.

```php
public __toString(): string
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### fromNative

Returns a Name objects form PHP native values.

```php
public static fromNative(): \Qubus\ValueObjects\Person\Name|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### getFirstName

Returns the first name.

```php
public getFirstName(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```












***

### getMiddleName

Returns the middle name.

```php
public getMiddleName(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```












***

### getLastName

Returns the last name.

```php
public getLastName(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```












***

### getFullName

Returns the full name.

```php
public getFullName(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### equals

Tells whether two names are equal by comparing their values.

```php
public equals(\Qubus\ValueObjects\Person\Name|\Qubus\ValueObjects\ValueObject $name): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **\Qubus\ValueObjects\Person\Name&#124;\Qubus\ValueObjects\ValueObject** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***


***
> Automatically generated on 2025-10-13
