# Where

***

* Full name: `\Qubus\Expressive\Where`

## Methods

### where

Add where condition, more calls appends with AND.

```php
public where(mixed $condition, mixed $parameters = null): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type      | Description                                                |
|---------------|-----------|------------------------------------------------------------|
| `$condition`  | **mixed** | condition possibly containing ? or :name                   |
| `$parameters` | **mixed** | array accepted by PDOStatement::execute or a scalar value. |

***

### wherePK

Where Primary key

```php
public wherePK(int|string $id): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$id`     | **int\|string** |             |

***

### whereNot

WHERE $columName != $value

```php
public whereNot(string $columnName, mixed $value): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |
| `$value`      | **mixed**  |             |

***

### whereLike

WHERE $columName LIKE $value

```php
public whereLike(string $columnName, mixed $value): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |
| `$value`      | **mixed**  |             |

***

### whereNotLike

WHERE $columName NOT LIKE $value

```php
public whereNotLike(string $columnName, mixed $value): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |
| `$value`      | **mixed**  |             |

***

### whereGt

WHERE $columName > $value

```php
public whereGt(string $columnName, mixed $value): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |
| `$value`      | **mixed**  |             |

***

### whereGte

WHERE $columName >= $value

```php
public whereGte(string $columnName, mixed $value): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |
| `$value`      | **mixed**  |             |

***

### whereLt

WHERE $columName < $value

```php
public whereLt(string $columnName, mixed $value): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |
| `$value`      | **mixed**  |             |

***

### whereLte

WHERE $columName <= $value

```php
public whereLte(string $columnName, mixed $value): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |
| `$value`      | **mixed**  |             |

***

### whereIn

WHERE $columName IN (?,?,?,...)

```php
public whereIn(string $columnName, list $values): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description                                       |
|---------------|------------|---------------------------------------------------|
| `$columnName` | **string** |                                                   |
| `$values`     | **list**   | An empty list produces an always-false predicate. |

***

### whereNotIn

WHERE $columName NOT IN (?,?,?,...)

```php
public whereNotIn(string $columnName, list $values): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description                      |
|---------------|------------|----------------------------------|
| `$columnName` | **string** |                                  |
| `$values`     | **list**   | An empty list adds no predicate. |

***

### whereNull

WHERE $columName IS NULL

```php
public whereNull(string $columnName): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |

***

### whereNotNull

WHERE $columName IS NOT NULL

```php
public whereNotNull(string $columnName): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |

***

### orderBy

ORDER BY $columnName (ASC \| DESC)

```php
public orderBy(string $columnName, string $ordering = 'ASC'): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description                              |
|---------------|------------|------------------------------------------|
| `$columnName` | **string** | - The name of the colum or an expression |
| `$ordering`   | **string** | `ASC` or `DESC`, case-insensitive.       |

**Throws:**

When the ordering is not `ASC` or `DESC`.
- [`QueryBuilderException`](./QueryBuilderException.md)

***

### limit

LIMIT $limit

```php
public limit(int|null $limit = null): \Qubus\Expressive\Database|int|null
```

**Parameters:**

| Parameter | Type          | Description                                                         |
|-----------|---------------|---------------------------------------------------------------------|
| `$limit`  | **int\|null** | A non-negative limit, including zero; null reads the current limit. |

***

### offset

OFFSET $offset

```php
public offset(int|null $offset = null): \Qubus\Expressive\Database|int|null
```

**Parameters:**

| Parameter | Type          | Description                                           |
|-----------|---------------|-------------------------------------------------------|
| `$offset` | **int\|null** | A non-negative offset; null reads the current offset. |

***

### pagination

```php
public pagination(int $perPage, int $page): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter  | Type    | Description |
|------------|---------|-------------|
| `$perPage` | **int** |             |
| `$page`    | **int** |             |

***

### and

Create an AND operator in the where clause

```php
public and(): \Qubus\Expressive\Database
```

***

### or

Create an OR operator in the where clause

```php
public or(): \Qubus\Expressive\Database
```

***

### wrap

To group multiple where clauses together.

```php
public wrap(): \Qubus\Expressive\Database
```

***
