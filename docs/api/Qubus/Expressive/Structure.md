# Structure

***

* Full name: `\Qubus\Expressive\Structure`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Properties

### primaryKey

```php
private string $primaryKey
```

***

### foreignKey

```php
private string $foreignKey
```

***

## Methods

### __construct

Structure constructor

```php
public __construct(string $primaryKey = 'id', string $foreignKey = '%s_id'): mixed
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$primaryKey` | **string** |             |
| `$foreignKey` | **string** |             |

***

### getPrimaryKey

```php
public getPrimaryKey(string $table): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$table`  | **string** |             |

***

### getForeignKey

```php
public getForeignKey(string $table): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$table`  | **string** |             |

***

### key

```php
private key(string $key, string $table): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |
| `$table`  | **string** |             |

***
