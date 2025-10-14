***

# Ulid





* Full name: `\Qubus\ValueObjects\Identity\Ulid`
* Parent class: [`\Qubus\ValueObjects\StringLiteral\StringLiteral`](../StringLiteral/StringLiteral.md)



## Properties


### value



```php
protected string $value
```






***

## Methods


### __construct

Returns a String object given a PHP native string as parameter.

```php
public __construct(?string $value = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **?string** |  |





***

### fromNative

Returns a String object given a PHP native string as parameter.

```php
public static fromNative(): \Qubus\ValueObjects\StringLiteral\StringLiteral|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### generateAsString

Generate a new Uuid string.

```php
public static generateAsString(): string
```



* This method is **static**.








***

### equals

Tells whether two Uuid are equal by comparing their values.

```php
public equals(\Qubus\ValueObjects\ValueObject $uuid): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uuid` | **\Qubus\ValueObjects\ValueObject** |  |





***


## Inherited methods


### fromNative

Returns a String object given a PHP native string as parameter.

```php
public static fromNative(): \Qubus\ValueObjects\StringLiteral\StringLiteral|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### __construct

Returns a String object given a PHP native string as parameter.

```php
public __construct(string $value): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **string** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### toNative

Returns the value of the string.

```php
public toNative(): string
```












***

### equals

Tells whether two strings are equal by comparing their values

```php
public equals(\Qubus\ValueObjects\StringLiteral\StringLiteral|\Qubus\ValueObjects\ValueObject $stringLiteral): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$stringLiteral` | **\Qubus\ValueObjects\StringLiteral\StringLiteral&#124;\Qubus\ValueObjects\ValueObject** |  |





***

### isEmpty

Tells whether the String is empty

```php
public isEmpty(): bool
```












***

### __toString

Returns the string value itself

```php
public __toString(): string
```












***


***
> Automatically generated on 2025-10-13
