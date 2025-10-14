***

# File





* Full name: `\Qubus\Http\Encryption\Env\File`




## Methods


### encrypt

Encrypts the input file's content,
and writes the encrypted data to
an output file.

```php
public static encrypt(string $input, mixed $output, \Defuse\Crypto\Key $key): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$input` | **string** |  |
| `$output` | **mixed** |  |
| `$key` | **\Defuse\Crypto\Key** |  |




**Throws:**

- [`EnvironmentIsBrokenException`](../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)



***

### decrypt

Decrypts the data from the input file
and returns the decrypted data.

```php
public static decrypt(string $input, \Defuse\Crypto\Key $key): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$input` | **string** |  |
| `$key` | **\Defuse\Crypto\Key** |  |




**Throws:**

- [`WrongKeyOrModifiedCiphertextException`](../../../../Defuse/Crypto/Exception/WrongKeyOrModifiedCiphertextException.md)

- [`EnvironmentIsBrokenException`](../../../../Defuse/Crypto/Exception/EnvironmentIsBrokenException.md)



***


***
> Automatically generated on 2025-10-13
