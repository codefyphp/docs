# PhpSession

***

* Full name: `\Qubus\Http\Session\PhpSession`

## Methods

### has

Checks if session exists.

```php
public has(string $name): bool
```

**Parameters:**

| Parameter | Type       | Description   |
|-----------|------------|---------------|
| `$name`   | **string** | Session name. |

***

### get

Retrieve session.

```php
public get(string $name): string|array
```

**Parameters:**

| Parameter | Type       | Description   |
|-----------|------------|---------------|
| `$name`   | **string** | Session name. |

***

### getAll

Returns all session data.

```php
public getAll(): array
```

***

### unsetSession

Destroy specific session data by key.

```php
public unsetSession(string $key): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***
