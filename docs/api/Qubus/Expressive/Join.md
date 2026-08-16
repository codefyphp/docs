# Join

***

* Full name: `\Qubus\Expressive\Join`

## Constants


| Constant           | Visibility | Type | Value         |
|--------------------|------------|------|---------------|
| `JOIN_INNER`       | public     |      | 'INNER'       |
| `JOIN_OUTER`       | public     |      | 'OUTER'       |
| `JOIN_LEFT`        | public     |      | 'LEFT'        |
| `JOIN_RIGHT`       | public     |      | 'RIGHT'       |
| `JOIN_RIGHT_OUTER` | public     |      | 'RIGHT OUTER' |
| `JOIN_LEFT_OUTER`  | public     |      | 'LEFT OUTER'  |

## Methods

### join

Build a join

```php
public join(string $tableName, string $constraint, string $tableAlias = '', string $joinOperator = \self::JOIN_LEFT): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter       | Type       | Description                   |
|-----------------|------------|-------------------------------|
| `$tableName`    | **string** |                               |
| `$constraint`   | **string** | -> id = profile.user_id       |
| `$tableAlias`   | **string** | - The alias of the table name |
| `$joinOperator` | **string** | - LEFT \| INNER \| etc...     |

***

### on

An alias to join by using a Database instance.

```php
public on(\Qubus\Expressive\Database $query, string $joinOperator = \self::JOIN_LEFT): \Qubus\Expressive\Database
```

The Database instance may have select and where statement for the ON clause

**Parameters:**

| Parameter       | Type                           | Description |
|-----------------|--------------------------------|-------------|
| `$query`        | **\Qubus\Expressive\Database** |             |
| `$joinOperator` | **string**                     |             |

***

### getJoinOnString

Create the JOIN ... ON string when there is a join. It will be called by on().

```php
public getJoinOnString(): string
```

***
