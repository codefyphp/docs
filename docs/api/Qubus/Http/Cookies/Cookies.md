# Cookies

***

* Full name: `\Qubus\Http\Cookies\Cookies`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Constants

| Constant        | Visibility | Type | Value    |
|-----------------|------------|------|----------|
| `COOKIE_HEADER` | public     |      | 'Cookie' |

## Properties

### cookies

```php
private \Qubus\Http\Cookies\CookieCollection[] $cookies
```

***

## Methods

### __construct

```php
public __construct(array|\Qubus\Http\Cookies\CookieCollection[] $cookies = []): mixed
```

**Parameters:**

| Parameter  | Type                                              | Description |
|------------|---------------------------------------------------|-------------|
| `$cookies` | **array\|\Qubus\Http\Cookies\CookieCollection[]** |             |

***

### has

Checks if cookie exists.

```php
public has(string $name): bool
```

**Parameters:**

| Parameter | Type       | Description  |
|-----------|------------|--------------|
| `$name`   | **string** | Cookie name. |

***

### get

Retrieve cookie from the collection.

```php
public get(string $name): ?\Qubus\Http\Cookies\CookieCollection
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### getAll

Returns a CookieCollection.

```php
public getAll(): array
```

***

### with

```php
public with(\Qubus\Http\Cookies\CookieCollection $cookie): \Qubus\Http\Cookies\Cookies
```

**Parameters:**

| Parameter | Type                                     | Description |
|-----------|------------------------------------------|-------------|
| `$cookie` | **\Qubus\Http\Cookies\CookieCollection** |             |

***

### without

```php
public without(string $name): \Qubus\Http\Cookies\Cookies
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### renderIntoCookieHeader

Render Cookies into a Request.

```php
public renderIntoCookieHeader(\Psr\Http\Message\RequestInterface $request): \Psr\Http\Message\RequestInterface
```

**Parameters:**

| Parameter  | Type                                   | Description |
|------------|----------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\RequestInterface** |             |

***

### fromCookieString

Create Cookies from a Cookie header value string.

```php
public static fromCookieString(string $string): self
```

* This method is **static**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$string` | **string** |             |

***

### fromRequest

Retrieves the cookie string.

```php
public static fromRequest(\Psr\Http\Message\RequestInterface $request): \Qubus\Http\Cookies\Cookies
```

* This method is **static**.
**Parameters:**

| Parameter  | Type                                   | Description |
|------------|----------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\RequestInterface** |             |

***
