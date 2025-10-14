***

# IPAddress





* Full name: `\Qubus\ValueObjects\Web\IPAddress`
* Parent class: [`\Qubus\ValueObjects\Web\Domain`](./Domain.md)




## Methods


### __construct

Returns a new IPAddress

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

### getVersion

Returns the version (IPv4 or IPv6) of the ip address

```php
public getVersion(): string
```












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

### specifyType

Returns a Hostname or a IPAddress object depending on passed value

```php
public static specifyType(mixed $domain): \Qubus\ValueObjects\Web\Hostname|\Qubus\ValueObjects\Web\IPAddress
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$domain` | **mixed** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***


***
> Automatically generated on 2025-10-13
