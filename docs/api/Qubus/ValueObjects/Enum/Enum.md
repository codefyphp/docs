***

# Enum





* Full name: `\Qubus\ValueObjects\Enum\Enum`
* Parent class: [`Enum`](../../../MabeEnum/Enum.md)
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md), [`\Serializable`](../../../Serializable.md)
* This class is an **Abstract class**




## Methods


### fromNative

Returns a new Enum object from passed value matching argument

```php
public static fromNative(): static
```



* This method is **static**.








***

### toNative

Returns the PHP native value of the enum

```php
public toNative(): mixed
```












***

### equals

Tells whether two Enum objects are sameValueAs by comparing their values

```php
public equals(\Qubus\ValueObjects\Enum\Enum|\Qubus\ValueObjects\ValueObject $enum): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$enum` | **\Qubus\ValueObjects\Enum\Enum&#124;\Qubus\ValueObjects\ValueObject** |  |





***

### __toString

Returns a native string representation of the Enum value

```php
public __toString(): string
```












***

### jsonSerialize



```php
public jsonSerialize(): array
```












***


***
> Automatically generated on 2025-10-13
