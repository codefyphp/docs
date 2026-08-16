# Aggregate

***

* Full name: `\Qubus\Expressive\Aggregate`

## Methods

### count

Return the aggregate count of column

```php
public count(string|null $column = null): float|int
```

**Parameters:**

| Parameter | Type             | Description       |
|-----------|------------------|-------------------|
| `$column` | **string\|null** | - the column name |

***

### max

Return the aggregate max count of column

```php
public max(string $column): float|int
```

**Parameters:**

| Parameter | Type       | Description       |
|-----------|------------|-------------------|
| `$column` | **string** | - the column name |

***

### min

Return the aggregate min count of column

```php
public min(string $column): float|int
```

**Parameters:**

| Parameter | Type       | Description       |
|-----------|------------|-------------------|
| `$column` | **string** | - the column name |

***

### sum

Return the aggregate sum count of column

```php
public sum(string $column): float|int
```

**Parameters:**

| Parameter | Type       | Description       |
|-----------|------------|-------------------|
| `$column` | **string** | - the column name |

***

### avg

Return the aggregate average count of column

```php
public avg(string $column): float|int
```

**Parameters:**

| Parameter | Type       | Description       |
|-----------|------------|-------------------|
| `$column` | **string** | - the column name |

***

### aggregate

```php
public aggregate(string $fn): float|int
```

**Parameters:**

| Parameter | Type       | Description                               |
|-----------|------------|-------------------------------------------|
| `$fn`     | **string** | - The function to use for the aggregation |

***
