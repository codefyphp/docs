# AuthUserRepository

***

* Full name: `\Codefy\Framework\Auth\Repository\AuthUserRepository`

## Methods

### authenticate

Authenticate with a user's credential
(email, username, or login token)
along with a password.

```php
public authenticate(string $credential, string|null $password = null): \Qubus\Http\Session\SessionEntity|null
```

**Parameters:**

| Parameter     | Type             | Description |
|---------------|------------------|-------------|
| `$credential` | **string**       |             |
| `$password`   | **string\|null** |             |

***

### find

Find a user by their token.

```php
public find(string $token): bool|object|null
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$token`  | **string** |             |

***
