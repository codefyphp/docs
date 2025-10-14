***

# UrlFragmentIdentifier





* Full name: `\Qubus\ValueObjects\Web\UrlFragmentIdentifier`
* Parent class: [`\Qubus\ValueObjects\StringLiteral\StringLiteral`](../StringLiteral/StringLiteral.md)
* This class implements:
[`\Qubus\ValueObjects\Web\FragmentIdentifier`](./FragmentIdentifier.md)




## Methods


### __construct

Returns a new FragmentIdentifier.

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
