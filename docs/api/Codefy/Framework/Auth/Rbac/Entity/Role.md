# Role

***

* Full name: `\Codefy\Framework\Auth\Rbac\Entity\Role`

## Methods

### addChild

```php
public addChild(\Codefy\Framework\Auth\Rbac\Entity\Role $role): void
```

**Parameters:**

| Parameter | Type                                        | Description |
|-----------|---------------------------------------------|-------------|
| `$role`   | **\Codefy\Framework\Auth\Rbac\Entity\Role** |             |

***

### removeChild

```php
public removeChild(string $roleName): void
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$roleName` | **string** |             |

***

### getChildren

```php
public getChildren(): \Codefy\Framework\Auth\Rbac\Entity\Role[]
```

***

### addPermission

```php
public addPermission(\Codefy\Framework\Auth\Rbac\Entity\Permission $permission): void
```

**Parameters:**

| Parameter     | Type                                              | Description |
|---------------|---------------------------------------------------|-------------|
| `$permission` | **\Codefy\Framework\Auth\Rbac\Entity\Permission** |             |

***

### removePermission

```php
public removePermission(string $permissionName): void
```

**Parameters:**

| Parameter         | Type       | Description |
|-------------------|------------|-------------|
| `$permissionName` | **string** |             |

***

### getPermissions

```php
public getPermissions(bool $withChildren = false): \Codefy\Framework\Auth\Rbac\Entity\Permission[]
```

**Parameters:**

| Parameter       | Type     | Description |
|-----------------|----------|-------------|
| `$withChildren` | **bool** |             |

***

### checkAccess

```php
public checkAccess(string $permissionName, array|null $params = null): bool
```

**Parameters:**

| Parameter         | Type            | Description |
|-------------------|-----------------|-------------|
| `$permissionName` | **string**      |             |
| `$params`         | **array\|null** |             |

**Throws:**

- [`SentinelException`](../Exception/SentinelException.md)

***
