***

# SameSite





* Full name: `\Qubus\Http\Cookies\SameSite`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`STRICT`|private| |&#039;Strict&#039;|
|`LAX`|private| |&#039;Lax&#039;|
|`NONE`|private| |&#039;None&#039;|

## Properties


### value



```php
private string $value
```






***

## Methods


### __construct



```php
private __construct(string $value): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **string** |  |





***

### strict



```php
public static strict(): self
```



* This method is **static**.








***

### lax



```php
public static lax(): self
```



* This method is **static**.








***

### none



```php
public static none(): self
```



* This method is **static**.








***

### fromString



```php
public static fromString(string $sameSite): self
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$sameSite` | **string** |  |




**Throws:**
<p>If the given SameSite string is neither strict, lax or none.</p>

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### asString



```php
public asString(): string
```












***


***
> Automatically generated on 2025-10-13
