# Validation

***

* Full name: `\Qubus\Http\Cookies\Validation\Validation`

## Constants

| Constant       | Visibility | Type | Value    |
|----------------|------------|------|----------|
| `DEFAULT_ALGO` | public     |      | 'sha256' |
| `NONCE_LENGTH` | public     |      | 32       |

## Properties

### key

```php
public string $key
```

***

### algo

```php
public string $algo
```

***

## Methods

### __construct

```php
public __construct(string $key, ?string $algo = null): mixed
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$key`    | **string**  |             |
| `$algo`   | **?string** |             |

***

### extract

```php
public extract(mixed $value): string
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### sign

```php
public sign(mixed $value): string|false
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### verify

```php
private verify(\Qubus\Http\Cookies\Validation\Message $message): bool
```

**Parameters:**

| Parameter  | Type                                       | Description |
|------------|--------------------------------------------|-------------|
| `$message` | **\Qubus\Http\Cookies\Validation\Message** |             |

***

### generateNonce

```php
private static generateNonce(): string
```

* This method is **static**.
***

### hashCompare

```php
private static hashCompare(mixed $hash1, mixed $hash2): bool
```

* This method is **static**.
**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$hash1`  | **mixed** |             |
| `$hash2`  | **mixed** |             |

***
