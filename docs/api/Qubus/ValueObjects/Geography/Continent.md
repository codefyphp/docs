***

# Continent





* Full name: `\Qubus\ValueObjects\Geography\Continent`
* Parent class: [`\Qubus\ValueObjects\Enum\Enum`](../Enum/Enum.md)


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`AFRICA`|public| |&#039;Africa&#039;|
|`EUROPE`|public| |&#039;Europe&#039;|
|`ASIA`|public| |&#039;Asia&#039;|
|`NORTH_AMERICA`|public| |&#039;North America&#039;|
|`SOUTH_AMERICA`|public| |&#039;South America&#039;|
|`ANTARCTICA`|public| |&#039;Antarctica&#039;|
|`AUSTRALIA`|public| |&#039;Australia&#039;|




## Inherited methods


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
