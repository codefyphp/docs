# QubusEncryption

***

* Full name: `\Qubus\Http\Encryption\Adapter\QubusEncryption`
* This class implements:
  [`\Qubus\Http\Encryption\Encryption`](../Encryption.md)

## Properties

### key

```php
public \Defuse\Crypto\Key $key
```

***

## Methods

### __construct

```php
public __construct(\Defuse\Crypto\Key $key): mixed
```

**Parameters:**

| Parameter | Type                   | Description |
|-----------|------------------------|-------------|
| `$key`    | **\Defuse\Crypto\Key** |             |

***

### decrypt

```php
public decrypt(string $value, bool $rawBinary = false): string
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$value`     | **string** |             |
| `$rawBinary` | **bool**   |             |

**Throws:**

- [`WrongKeyOrModifiedCiphertextException`](../../../../Defuse/Crypto/Exception/WrongKeyOrModifiedCiphertextException.md)
- [`EnvironmentIsBrokenException`](../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)

***

### encrypt

```php
public encrypt(string $value, bool $rawBinary = false): string
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$value`     | **string** |             |
| `$rawBinary` | **bool**   |             |

**Throws:**

- [`EnvironmentIsBrokenException`](../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)

***
