***

# CookieCollection





* Full name: `\Qubus\Http\Cookies\CookieCollection`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### name



```php
private ?string $name
```






***

### value



```php
private ?string $value
```






***

## Methods


### __construct



```php
public __construct(string $name, ?string $value = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$value` | **?string** |  |





***

### getName

Get cookie name.

```php
public getName(): ?string
```












***

### getValue

Get cookie value.

```php
public getValue(): ?string
```












***

### withValue

Sets cookie value

```php
public withValue(?string $value = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **?string** |  |





***

### __toString

Render Cookie as a string.

```php
public __toString(): string
```












***

### create

Create a cookie.

```php
public static create(string $name, string|null $value = null): self
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | Cookie name. |
| `$value` | **string&#124;null** | Cookie value. |





***

### listFromCookieString

Create a list of Cookies from a Cookie header value string.

```php
public static listFromCookieString(string $string): self[]
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |





***

### oneFromCookiePair

Create one Cookie from a cookie key/value header value string.

```php
public static oneFromCookiePair(string $string): self
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |





***


***
> Automatically generated on 2025-10-13
