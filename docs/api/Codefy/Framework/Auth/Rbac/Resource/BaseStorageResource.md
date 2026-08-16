# BaseStorageResource

***

* Full name: `\Codefy\Framework\Auth\Rbac\Resource\BaseStorageResource`
* This class implements:
  [`\Codefy\Framework\Auth\Rbac\Resource\StorageResource`](./StorageResource.md)
* This class is an **Abstract class**

## Properties

### roles

```php
public array $roles
```

***

### permissions

```php
public array $permissions
```

***

## Methods

### addRole

```php
public addRole(string $name, string $description = ''): \Codefy\Framework\Auth\Rbac\Entity\Role
```

**Parameters:**

| Parameter      | Type       | Description |
|----------------|------------|-------------|
| `$name`        | **string** |             |
| `$description` | **string** |             |

**Throws:**

- [`SentinelException`](../Exception/SentinelException.md)

***

### addPermission

```php
public addPermission(string $name, string $description = ''): \Codefy\Framework\Auth\Rbac\Entity\Permission
```

**Parameters:**

| Parameter      | Type       | Description |
|----------------|------------|-------------|
| `$name`        | **string** |             |
| `$description` | **string** |             |

***

### getRole

```php
public getRole(string $name): ?\Codefy\Framework\Auth\Rbac\Entity\Role
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### deleteRole

```php
public deleteRole(string $name): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### getPermission

```php
public getPermission(string $name): ?\Codefy\Framework\Auth\Rbac\Entity\Permission
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### deletePermission

```php
public deletePermission(string $name): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### clear

```php
public clear(): void
```

***
