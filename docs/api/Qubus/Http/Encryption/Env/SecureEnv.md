# SecureEnv

***

* Full name: `\Qubus\Http\Encryption\Env\SecureEnv`

## Methods

### parse

```php
public static parse(string $inputFile, string $keyFile): void
```

* This method is **static**.
**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$inputFile` | **string** |             |
| `$keyFile`   | **string** |             |

**Throws:**

- [`EnvironmentIsBrokenException`](../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)
- [`WrongKeyOrModifiedCiphertextException`](../../../../Defuse/Crypto/Exception/WrongKeyOrModifiedCiphertextException.md)
- [`BadFormatException`](../../../../Defuse/Crypto/Exception/BadFormatException.md)

***
