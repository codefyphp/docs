# Insert

***

* Full name: `\Qubus\Expressive\Insert`

## Methods

### returning

Returning (Postgres etc.)

```php
public returning(string $cols = '*'): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$cols`   | **string** |             |

***

### upsert

Upsert (basic support)

```php
public upsert(list<string> $conflictCols, array<string,mixed> $updateData): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter       | Type                    | Description |
|-----------------|-------------------------|-------------|
| `$conflictCols` | **list<string>**        |             |
| `$updateData`   | **array<string,mixed>** |             |

***

### lastInsertId

Retrieves the ID of the last record inserted.

```php
public lastInsertId(string|null $pk = null): string|false
```

**Parameters:**

| Parameter | Type             | Description |
|-----------|------------------|-------------|
| `$pk`     | **string\|null** |             |

***

### insert

Insert one or more rows. Bulk rows must contain identical columns in identical order.

```php
public insert(array<string,mixed>|list<array<string,mixed>> $data): \Qubus\Expressive\Database|int
```

If a single row is inserted, its row instance is returned. Bulk inserts return the affected row count.

**Parameters:**

| Parameter | Type                                               | Description     |
|-----------|----------------------------------------------------|-----------------|
| `$data`   | **array<string,mixed>\|list<array<string,mixed>>** | Data to insert. |

**Throws:**

When the payload is empty or bulk rows have inconsistent columns.
- [`QueryBuilderException`](./QueryBuilderException.md)

***
