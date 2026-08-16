# RbacRole

***

* Full name: `\Codefy\Framework\Auth\Rbac\Entity\RbacRole`
* This class implements:
  [`\Codefy\Framework\Auth\Rbac\Entity\Role`](./Role.md)

## Properties

### childrenNames

```php
protected array $childrenNames
```

***

### permissionNames

```php
protected array $permissionNames
```

***

### name

```php
public string $name
```

***

### description

```php
public string $description
```

***

### rbacStorageCollection

```php
protected \Codefy\Framework\Auth\Rbac\Resource\StorageResource $rbacStorageCollection
```

***

## Methods

### __construct

```php
public __construct(string $name, string $description, \Codefy\Framework\Auth\Rbac\Resource\StorageResource $rbacStorageCollection): mixed
```

**Parameters:**

| Parameter                | Type                                                     | Description |
|--------------------------|----------------------------------------------------------|-------------|
| `$name`                  | **string**                                               |             |
| `$description`           | **string**                                               |             |
| `$rbacStorageCollection` | **\Codefy\Framework\Auth\Rbac\Resource\StorageResource** |             |

***

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
public checkAccess(string $permissionName, ?array $params = null): bool
```

**Parameters:**

| Parameter         | Type       | Description |
|-------------------|------------|-------------|
| `$permissionName` | **string** |             |
| `$params`         | **?array** |             |

***

### collectChildrenPermissions

```php
protected collectChildrenPermissions(\Codefy\Framework\Auth\Rbac\Entity\Permission $permission, mixed& $result): void
```

**Parameters:**

| Parameter     | Type                                              | Description |
|---------------|---------------------------------------------------|-------------|
| `$permission` | **\Codefy\Framework\Auth\Rbac\Entity\Permission** |             |
| `$result`     | **mixed**                                         |             |

***
