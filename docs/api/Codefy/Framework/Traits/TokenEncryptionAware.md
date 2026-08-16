# TokenEncryptionAware

***

* Full name: `\Codefy\Framework\Traits\TokenEncryptionAware`

## Properties

### key

```php
protected ?string $key
```

***

## Methods

### sign

Sign the value.

```php
protected sign(string $value): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$value`  | **string** |             |

**Throws:**

- [`EnvironmentIsBrokenException`](../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)
- [`BadFormatException`](../../../Defuse/Crypto/Exception/BadFormatException.md)

***
### unsign

Unsign the value.

```php
protected unsign(string $value): string
```

**Parameters:**

| Parameter | Type       | Description      |
|-----------|------------|------------------|
| `$value`  | **string** | Encrypted value. |

**Return Value:**

Return the value if signature is valid.

**Throws:**

- [`BadFormatException`](../../../Defuse/Crypto/Exception/BadFormatException.md)
- [`EnvironmentIsBrokenException`](../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)
- [`WrongKeyOrModifiedCiphertextException`](../../../Defuse/Crypto/Exception/WrongKeyOrModifiedCiphertextException.md)

***
### compareTokens

```php
protected compareTokens(string $knownString, string $userString): bool
```

**Parameters:**

| Parameter      | Type       | Description |
|----------------|------------|-------------|
| `$knownString` | **string** |             |
| `$userString`  | **string** |             |

***
