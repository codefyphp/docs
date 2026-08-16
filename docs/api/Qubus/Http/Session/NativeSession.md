# NativeSession

***

* Full name: `\Qubus\Http\Session\NativeSession`
* This class implements:
  [`\Qubus\Http\Session\PhpSession`](./PhpSession.md)

## Constants

| Constant          | Visibility | Type | Value                                                                                                                                                                                                                                                                       |
|-------------------|------------|------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SESSION_OPTIONS` | protected  |      | ['use_cookies' => 1, 'cookie_secure' => 1, 'cookie_lifetime' => 360, 'cookie_path' => '/', 'cookie_domain' => '', 'use_only_cookies' => 1, 'cookie_httponly' => 1, 'use_strict_mode' => 1, 'cache_limiter' => 'nocache', 'cache_expire' => 180, 'cookie_samesite' => 'Lax'] |

## Properties

### started

```php
protected bool $started
```

***

### config

```php
protected \Qubus\Config\ConfigContainer $config
```

***

### sessionId

```php
protected ?string $sessionId
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Config\ConfigContainer $config, ?\SessionHandlerInterface $handler = null, ?string $sessionId = null): mixed
```

**Parameters:**

| Parameter    | Type                              | Description |
|--------------|-----------------------------------|-------------|
| `$config`    | **\Qubus\Config\ConfigContainer** |             |
| `$handler`   | **?\SessionHandlerInterface**     |             |
| `$sessionId` | **?string**                       |             |

***

### has

Checks if session exists.

```php
public has(string $name): bool
```

**Parameters:**

| Parameter | Type       | Description   |
|-----------|------------|---------------|
| `$name`   | **string** | Session name. |

**Throws:**

- [`SessionException`](./SessionException.md)

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

**Throws:**

- [`SessionException`](./SessionException.md)

***

### set

Sets the session.

```php
public set(string $name, mixed $value): void
```

**Parameters:**

| Parameter | Type       | Description               |
|-----------|------------|---------------------------|
| `$name`   | **string** | Session name.             |
| `$value`  | **mixed**  | Value of the session set. |

**Throws:**

- [`SessionException`](./SessionException.md)

***

### configOptions

Returns an array of session configOptions.

```php
public configOptions(): array
```

**Throws:**

- [`Exception`](../../Exception/Exception.md)

***

### isSessionActive

Returns true if sessions are enabled, and one exists.

```php
public isSessionActive(): bool
```

***

### sessionId

Returns the current session id if it exists. If not, it will be set.

```php
public sessionId(string|null $id = null): string|null
```

**Parameters:**

| Parameter | Type             | Description        |
|-----------|------------------|--------------------|
| `$id`     | **string\|null** | Id of the session. |

***

### regenerateId

Updates the current session ID with a new one.

```php
public regenerateId(): void
```

**Throws:**

- [`SessionException`](./SessionException.md)

***

### startSession

Starts a new session or resumes an existing session.

```php
public startSession(): void
```

**Throws:**

- [`SessionException`](./SessionException.md)

***

### currentSessionName

Returns the current session name.

```php
public currentSessionName(): string
```

***

### destroySession

Destroys all session data.

```php
public destroySession(): void
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

**Throws:**

- [`SessionException`](./SessionException.md)

***

### getAll

Returns all session data.

```php
public getAll(): array
```

**Throws:**

- [`SessionException`](./SessionException.md)

***

### clear

```php
public clear(): void
```

**Throws:**

- [`SessionException`](./SessionException.md)

***

### getCookieParameters

Returns the session cookie parameters.

```php
public getCookieParameters(): array
```

***
