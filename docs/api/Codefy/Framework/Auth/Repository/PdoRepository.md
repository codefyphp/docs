***

# PdoRepository





* Full name: `\Codefy\Framework\Auth\Repository\PdoRepository`
* This class implements:
[`\Codefy\Framework\Auth\Repository\AuthUserRepository`](./AuthUserRepository.md)



## Properties


### connection



```php
private \Qubus\Expressive\Connection $connection
```






***

### config



```php
protected \Qubus\Config\ConfigContainer $config
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Expressive\Connection $connection, \Qubus\Config\ConfigContainer $config): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$connection` | **\Qubus\Expressive\Connection** |  |
| `$config` | **\Qubus\Config\ConfigContainer** |  |





***

### authenticate

Authenticate with a user's credential
(email, username, or login token)
along with a password.

```php
public authenticate(string $credential, ?string $password = null): \Qubus\Http\Session\SessionEntity|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$credential` | **string** |  |
| `$password` | **?string** |  |




**Throws:**

- [`Exception`](../../../../Qubus/Exception/Exception.md)



***


***
> Automatically generated on 2025-10-13
