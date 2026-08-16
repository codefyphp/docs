# StorageResource

***

* Full name: `\Codefy\Framework\Auth\Rbac\Resource\StorageResource`
* Parent interfaces:
  [`\Codefy\Framework\Auth\Rbac\Guard`](../Guard.md)

## Methods

### load

```php
public load(): void
```

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

**Throws:**

- [`SentinelException`](../Exception/SentinelException.md)

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

### save

```php
public save(): void
```

**Throws:**

- [`SentinelException`](../Exception/SentinelException.md)

***
