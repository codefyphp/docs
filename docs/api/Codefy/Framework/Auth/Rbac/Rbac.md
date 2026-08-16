# Rbac

***

* Full name: `\Codefy\Framework\Auth\Rbac\Rbac`
* This class implements:
  [`\Codefy\Framework\Auth\Rbac\Guard`](./Guard.md)

## Properties

### storageResource

```php
protected \Codefy\Framework\Auth\Rbac\Resource\StorageResource $storageResource
```

***

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

### __construct

```php
public __construct(\Codefy\Framework\Auth\Rbac\Resource\StorageResource $storageResource): mixed
```

**Parameters:**

| Parameter          | Type                                                     | Description |
|--------------------|----------------------------------------------------------|-------------|
| `$storageResource` | **\Codefy\Framework\Auth\Rbac\Resource\StorageResource** |             |

***

### addRole

```php
public addRole(string $name, string $description = ''): \Codefy\Framework\Auth\Rbac\Entity\Role
```

**Parameters:**

| Parameter      | Type       | Description |
|----------------|------------|-------------|
| `$name`        | **string** |             |
| `$description` | **string** |             |

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
public getRole(string $name): \Codefy\Framework\Auth\Rbac\Entity\Role|null
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
public getPermission(string $name): \Codefy\Framework\Auth\Rbac\Entity\Permission|null
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

### load

```php
private load(): void
```

***

### save

```php
public save(): void
```

***
