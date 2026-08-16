# SameSite

***

* Full name: `\Qubus\Http\Cookies\SameSite`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Constants

| Constant | Visibility | Type | Value    |
|----------|------------|------|----------|
| `STRICT` | private    |      | 'Strict' |
| `LAX`    | private    |      | 'Lax'    |
| `NONE`   | private    |      | 'None'   |

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

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$value`  | **string** |             |

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

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$sameSite` | **string** |             |

**Throws:**

If the given SameSite string is neither strict, lax or none.
- [`TypeException`](../../Exception/Data/TypeException.md)

***

### asString

```php
public asString(): string
```

***
