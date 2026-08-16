# Gate

***

* Full name: `\Codefy\Framework\Auth\Gate`

## Properties

### rbac

```php
protected \Codefy\Framework\Auth\Rbac\Rbac $rbac
```

***

### user

```php
protected \Codefy\Framework\Auth\Repository\AuthUserRepository $user
```

***

## Methods

### __construct

```php
public __construct(\Codefy\Framework\Auth\Rbac\Rbac $rbac, \Codefy\Framework\Auth\Repository\AuthUserRepository $user): mixed
```

**Parameters:**

| Parameter | Type                                                     | Description |
|-----------|----------------------------------------------------------|-------------|
| `$rbac`   | **\Codefy\Framework\Auth\Rbac\Rbac**                     |             |
| `$user`   | **\Codefy\Framework\Auth\Repository\AuthUserRepository** |             |

***

### can

Authorization check.

```php
public can(string $permissionName, array $ruleParams = []): bool
```

**Parameters:**

| Parameter         | Type       | Description |
|-------------------|------------|-------------|
| `$permissionName` | **string** |             |
| `$ruleParams`     | **array**  |             |

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)
- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### current

Get the current authenticated user model.

```php
public current(): object|bool|null
```

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

***

### hasAuthenticatedUser

Whether user is authenticated.

```php
private hasAuthenticatedUser(): bool
```

***

### resolveUserByToken

```php
private resolveUserByToken(string $token): object|bool|null
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$token`  | **string** |             |

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

***

### getRoles

```php
private getRoles(): array
```

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

***

### guest

A guest is any user without an authenticated token.

```php
public guest(): bool
```

***

### isLoggedIn

Whether user is logged in.

```php
public isLoggedIn(): bool
```

***

### getToken

Fetch decrypted token from request context.

```php
private getToken(): ?string
```

***

### getRequest

Return request object.

```php
private getRequest(): \Psr\Http\Message\ServerRequestInterface|null
```

***
