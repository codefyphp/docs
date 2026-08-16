# CookieFactory

***

* Full name: `\Qubus\Http\Cookies\Factory\CookieFactory`
* This class implements:
  [`\Qubus\Http\Cookies\Factory\HttpCookieFactory`](./HttpCookieFactory.md)

## Properties

### config

```php
protected \Qubus\Config\ConfigContainer $config
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Config\ConfigContainer $config): mixed
```

**Parameters:**

| Parameter | Type                              | Description |
|-----------|-----------------------------------|-------------|
| `$config` | **\Qubus\Config\ConfigContainer** |             |

***

### make

Make a new cookie instance.

```php
public make(string $name, ?string $value = null, ?int $maxAge = null): \Qubus\Http\Cookies\SetCookieCollection
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$name`   | **string**  |             |
| `$value`  | **?string** |             |
| `$maxAge` | **?int**    |             |

***

### expire

Make an expired cookie instance.

```php
public expire(string $name): \Qubus\Http\Cookies\SetCookieCollection|string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### path

The cookie path. Default: '/'.

```php
public path(): string|null
```

**Throws:**

- [`Exception`](../../../Exception/Exception.md)

***

### domain

The cookie domain.

```php
public domain(): string
```

**Throws:**

- [`Exception`](../../../Exception/Exception.md)

***

### secure

```php
public secure(): bool
```

**Throws:**

- [`Exception`](../../../Exception/Exception.md)

***

### samesite

Cookie samesite. Default: 'lax'.

```php
public samesite(): string
```

**Throws:**

- [`Exception`](../../../Exception/Exception.md)

***

### config

```php
public config(): \Qubus\Config\ConfigContainer
```

***
