# ParsePdoDsn

***

* Full name: `\Qubus\Expressive\ParsePdoDsn`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Constants

| Constant         | Visibility | Type | Value                            |
|------------------|------------|------|----------------------------------|
| `SQLITE_DRIVERS` | private    |      | ['sqlite', 'sqlite2', 'sqlite3'] |

## Properties

### driver

```php
private string $driver
```

***

### parameters

```php
private array $parameters
```

***

### path

```php
private ?string $path
```

***

## Methods

### __construct

```php
public __construct(string $driver, array $parameters = [], ?string $path = null): mixed
```

**Parameters:**

| Parameter     | Type        | Description |
|---------------|-------------|-------------|
| `$driver`     | **string**  |             |
| `$parameters` | **array**   |             |
| `$path`       | **?string** |             |

***

### fromString

```php
public static fromString(string $dsn): self
```

* This method is **static**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$dsn`    | **string** |             |

***

### fromPdoDsn

```php
private static fromPdoDsn(string $dsn): self
```

* This method is **static**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$dsn`    | **string** |             |

***

### fromUri

```php
private static fromUri(string $uri): self
```

* This method is **static**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$uri`    | **string** |             |

***

### driver

```php
public driver(): string
```

***

### isSqlite

```php
public isSqlite(): bool
```

***

### host

```php
public host(): ?string
```

***

### port

```php
public port(): ?int
```

***

### database

```php
public database(): ?string
```

***

### path

```php
public path(): ?string
```

***

### username

```php
public username(): ?string
```

***

### password

```php
public password(): ?string
```

***

### charset

```php
public charset(): ?string
```

***

### get

```php
public get(string $key, mixed $default = null): mixed
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$key`     | **string** |             |
| `$default` | **mixed**  |             |

***

### has

```php
public has(string $key): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### parameters

```php
public parameters(): array
```

***

### toArray

```php
public toArray(): array
```

***

### toPdoDsn

```php
public toPdoDsn(): string
```

***

### toString

```php
public toString(): string
```

***

### __toString

```php
public __toString(): string
```

***

### isSqliteDriver

```php
private static isSqliteDriver(string $driver): bool
```

* This method is **static**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$driver` | **string** |             |

***
