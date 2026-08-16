# RbacLoader

***

* Full name: `\Codefy\Framework\Auth\Rbac\RbacLoader`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Properties

### rbac

```php
private \Codefy\Framework\Auth\Rbac\Rbac $rbac
```

***

### configContainer

```php
private \Qubus\Config\ConfigContainer $configContainer
```

***

## Methods

### __construct

```php
public __construct(\Codefy\Framework\Auth\Rbac\Rbac $rbac, \Qubus\Config\ConfigContainer $configContainer): mixed
```

**Parameters:**

| Parameter          | Type                                 | Description |
|--------------------|--------------------------------------|-------------|
| `$rbac`            | **\Codefy\Framework\Auth\Rbac\Rbac** |             |
| `$configContainer` | **\Qubus\Config\ConfigContainer**    |             |

***

### initRbacRoles

```php
public initRbacRoles(): void
```

**Throws:**

- [`Exception`](../../../../Qubus/Exception/Exception.md)

***

### initRbacPermissions

```php
public initRbacPermissions(): void
```

**Throws:**

- [`Exception`](../../../../Qubus/Exception/Exception.md)

***

### addRoles

```php
private addRoles(array $rolesConfig, ?\Codefy\Framework\Auth\Rbac\Entity\Role $parent = null): void
```

**Parameters:**

| Parameter      | Type                                         | Description |
|----------------|----------------------------------------------|-------------|
| `$rolesConfig` | **array**                                    |             |
| `$parent`      | **?\Codefy\Framework\Auth\Rbac\Entity\Role** |             |

***

### addPermissions

```php
private addPermissions(array $permissionsConfig, ?\Codefy\Framework\Auth\Rbac\Entity\Permission $parent = null): void
```

**Parameters:**

| Parameter            | Type                                               | Description |
|----------------------|----------------------------------------------------|-------------|
| `$permissionsConfig` | **array**                                          |             |
| `$parent`            | **?\Codefy\Framework\Auth\Rbac\Entity\Permission** |             |

**Throws:**

- [`SentinelException`](./Exception/SentinelException.md)

***
