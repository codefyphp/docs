# CsrfSession

***

* Full name: `\Codefy\Framework\Http\Middleware\Csrf\CsrfSession`
* This class is marked as **final** and can't be subclassed
* This class implements:
  `SessionEntity`
* This class is a **Final class**

## Properties

### csrfToken

```php
public ?string $csrfToken
```

***

## Methods

### withCsrfToken

```php
public withCsrfToken(?string $csrfToken = null): self
```

**Parameters:**

| Parameter    | Type        | Description |
|--------------|-------------|-------------|
| `$csrfToken` | **?string** |             |

***

### equals

```php
public equals(string $token): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$token`  | **string** |             |

***

### csrfToken

```php
public csrfToken(): string|null
```

***

### clear

```php
public clear(): void
```

***

### isEmpty

```php
public isEmpty(): bool
```

***
