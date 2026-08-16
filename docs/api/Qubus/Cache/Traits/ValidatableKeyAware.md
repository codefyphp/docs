# ValidatableKeyAware

***

* Full name: `\Qubus\Cache\Traits\ValidatableKeyAware`

## Methods

### reservedKeyCharacters

Reserved key characters that should not be used in a cache key.

```php
final public reservedKeyCharacters(): string
```

* This method is **final**.
***
### validateKey

Validates cache key.

```php
protected validateKey(string $key): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

**Throws:**

- [`TypeException`](../TypeException.md)

***
### isHashed

Checks if key is hashed.

```php
protected isHashed(string $key): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***
### prefix

Affixes a prefix to the

```php
protected prefix(string $key): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***
### validateKeys

Validates an array of keys.

```php
protected validateKeys(array $keys): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$keys`   | **array** |             |

**Throws:**

- [`TypeException`](../TypeException.md)

***
