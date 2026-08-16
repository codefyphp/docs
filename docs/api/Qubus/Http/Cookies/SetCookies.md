# SetCookies

***

* Full name: `\Qubus\Http\Cookies\SetCookies`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Constants

| Constant            | Visibility | Type | Value        |
|---------------------|------------|------|--------------|
| `SET_COOKIE_HEADER` | public     |      | 'Set-Cookie' |

## Properties

### setCookies

```php
private \Qubus\Http\Cookies\SetCookieCollection[] $setCookies
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Http\Cookies\SetCookieCollection[] $setCookies = []): mixed
```

**Parameters:**

| Parameter     | Type                                          | Description |
|---------------|-----------------------------------------------|-------------|
| `$setCookies` | **\Qubus\Http\Cookies\SetCookieCollection[]** |             |

***

### has

```php
public has(string $name): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### get

```php
public get(string $name): ?\Qubus\Http\Cookies\SetCookieCollection
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### getAll

```php
public getAll(): \Qubus\Http\Cookies\SetCookieCollection[]
```

***

### with

```php
public with(\Qubus\Http\Cookies\SetCookieCollection $setCookie): \Qubus\Http\Cookies\SetCookies
```

**Parameters:**

| Parameter    | Type                                        | Description |
|--------------|---------------------------------------------|-------------|
| `$setCookie` | **\Qubus\Http\Cookies\SetCookieCollection** |             |

***

### without

```php
public without(string $name): \Qubus\Http\Cookies\SetCookies
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### renderIntoSetCookieHeader

Render SetCookies into a Response.

```php
public renderIntoSetCookieHeader(\Psr\Http\Message\ResponseInterface $response): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter   | Type                                    | Description |
|-------------|-----------------------------------------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |             |

***

### fromSetCookieStrings

Create SetCookies from a collection of SetCookieCollection header value strings.

```php
public static fromSetCookieStrings(string[] $setCookieStrings): static
```

* This method is **static**.
**Parameters:**

| Parameter           | Type         | Description |
|---------------------|--------------|-------------|
| `$setCookieStrings` | **string[]** |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***

### fromResponse

Create SetCookies from a Response.

```php
public static fromResponse(\Psr\Http\Message\ResponseInterface $response): \Qubus\Http\Cookies\SetCookies
```

* This method is **static**.
**Parameters:**

| Parameter   | Type                                    | Description |
|-------------|-----------------------------------------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |             |

***
