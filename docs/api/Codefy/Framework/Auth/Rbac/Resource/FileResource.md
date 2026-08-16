# FileResource

***

* Full name: `\Codefy\Framework\Auth\Rbac\Resource\FileResource`
* Parent class: [`\Codefy\Framework\Auth\Rbac\Resource\BaseStorageResource`](./BaseStorageResource.md)

## Properties

### file

```php
protected string $file
```

***

## Methods

### __construct

```php
public __construct(string $file): mixed
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$file`   | **string** |             |

***

### load

```php
public load(): void
```

**Throws:**

- [`SentinelException`](../Exception/SentinelException.md)
- [`FilesystemException`](../../../../../League/Flysystem/FilesystemException.md)

***

### save

```php
public save(): void
```

**Throws:**

- [`FilesystemException`](../../../../../League/Flysystem/FilesystemException.md)

***

### roleToRow

```php
protected roleToRow(\Codefy\Framework\Auth\Rbac\Entity\Role $role): array
```

**Parameters:**

| Parameter | Type                                        | Description |
|-----------|---------------------------------------------|-------------|
| `$role`   | **\Codefy\Framework\Auth\Rbac\Entity\Role** |             |

***

### permissionToRow

```php
protected permissionToRow(\Codefy\Framework\Auth\Rbac\Entity\Permission $permission): array
```

**Parameters:**

| Parameter     | Type                                              | Description |
|---------------|---------------------------------------------------|-------------|
| `$permission` | **\Codefy\Framework\Auth\Rbac\Entity\Permission** |             |

***

### restorePermissions

```php
protected restorePermissions(array $permissionsData): void
```

**Parameters:**

| Parameter          | Type      | Description |
|--------------------|-----------|-------------|
| `$permissionsData` | **array** |             |

**Throws:**

- [`SentinelException`](../Exception/SentinelException.md)

***

### restoreRoles

```php
protected restoreRoles(array $rolesData): void
```

**Parameters:**

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `$rolesData` | **array** |             |

**Throws:**

- [`SentinelException`](../Exception/SentinelException.md)

***

## Inherited methods

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
