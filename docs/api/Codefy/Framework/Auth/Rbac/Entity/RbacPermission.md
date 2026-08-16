# RbacPermission

***

* Full name: `\Codefy\Framework\Auth\Rbac\Entity\RbacPermission`
* This class implements:
  [`\Codefy\Framework\Auth\Rbac\Entity\Permission`](./Permission.md)

## Properties

### childrenNames

```php
protected array $childrenNames
```

***

### ruleClass

```php
protected ?string $ruleClass
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
public addChild(\Codefy\Framework\Auth\Rbac\Entity\Permission $permission): void
```

**Parameters:**

| Parameter     | Type                                              | Description |
|---------------|---------------------------------------------------|-------------|
| `$permission` | **\Codefy\Framework\Auth\Rbac\Entity\Permission** |             |

***

### removeChild

```php
public removeChild(string $permissionName): void
```

**Parameters:**

| Parameter         | Type       | Description |
|-------------------|------------|-------------|
| `$permissionName` | **string** |             |

***

### getChildren

```php
public getChildren(): \Codefy\Framework\Auth\Rbac\Entity\Permission[]
```

***

### setRuleClass

```php
public setRuleClass(string $ruleClass): void
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$ruleClass` | **string** |             |

***

### getRuleClass

```php
public getRuleClass(): string|null
```

***

### checkAccess

```php
public checkAccess(?array $params = null): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$params` | **?array** |             |

**Throws:**

- [`SentinelException`](../Exception/SentinelException.md)

***
