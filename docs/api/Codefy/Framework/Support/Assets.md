# Assets

***

* Full name: `\Codefy\Framework\Support\Assets`
* Parent class: [`Assets`](../../../Qubus/Support/Assets.md)
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Properties

### codefy

```php
protected \Codefy\Framework\Application $codefy
```

***

## Methods

### __construct

```php
public __construct(\Codefy\Framework\Application $codefy, array $options = []): mixed
```

**Parameters:**

| Parameter  | Type                              | Description |
|------------|-----------------------------------|-------------|
| `$codefy`  | **\Codefy\Framework\Application** |             |
| `$options` | **array**                         |             |

***

### group

Get the instance of the assets manager for a given group.

```php
public group(string $group = 'default'): \Codefy\Framework\Support\Assets
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$group`  | **string** |             |

***
