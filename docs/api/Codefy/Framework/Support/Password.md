***

# Password





* Full name: `\Codefy\Framework\Support\Password`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**




## Methods


### algorithm

Algorithm to use when hashing the password (i.e. PASSWORD_DEFAULT, PASSWORD_ARGON2ID).

```php
private static algorithm(): string
```



* This method is **static**.





**Return Value:**

Password algorithm.



**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)



***

### options

An associative array containing options.

```php
private static options(): array
```



* This method is **static**.





**Return Value:**

Array of options.



**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)



***

### hash

Hashes a plain text password.

```php
public static hash(string $password): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$password` | **string** | Plain text password |


**Return Value:**

Hashed password.



**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)



***

### verify

Checks if the given hash matches the given options.

```php
public static verify(string $password, string $hash): bool
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$password` | **string** |  |
| `$hash` | **string** |  |





***

### needsRehash

Checks if the given hash matches the given algorithm and options provider.

```php
public static needsRehash(string $hash): bool
```

If not, it is assumed that the hash needs to be rehashed.

* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$hash` | **string** |  |




**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)



***

### algos

Get available password hashing algorithm IDs.

```php
public static algos(): array
```



* This method is **static**.








***

### getInfo

Returns information about the given hash.

```php
public static getInfo(string $password): array
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$password` | **string** |  |





***


***
> Automatically generated on 2025-10-13
