# Permission

***

* Full name: `\Codefy\Framework\Auth\Rbac\Entity\Permission`

## Methods

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
public setRuleClass(class-string|string $ruleClass): void
```

**Parameters:**

| Parameter    | Type                     | Description |
|--------------|--------------------------|-------------|
| `$ruleClass` | **class-string\|string** |             |

***

### getRuleClass

```php
public getRuleClass(): string|null
```

***

### checkAccess

```php
public checkAccess(array|null $params = null): bool
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$params` | **array\|null** |             |

***
