# Connection

***

* Full name: `\Qubus\Expressive\Connection`

## Methods

### query

```php
public query(string $sql, array<int|string,scalar|null> $params = []): \Qubus\Expressive\ResultSet
```

**Parameters:**

| Parameter | Type                                | Description |
|-----------|-------------------------------------|-------------|
| `$sql`    | **string**                          |             |
| `$params` | **array<int\|string,scalar\|null>** |             |

***

### command

```php
public command(string $sql, array<int|string,scalar|null> $params = []): bool
```

**Parameters:**

| Parameter | Type                                | Description |
|-----------|-------------------------------------|-------------|
| `$sql`    | **string**                          |             |
| `$params` | **array<int\|string,scalar\|null>** |             |

***

### column

```php
public column(string $sql, array<int|string,scalar|null> $params = []): mixed
```

**Parameters:**

| Parameter | Type                                | Description |
|-----------|-------------------------------------|-------------|
| `$sql`    | **string**                          |             |
| `$params` | **array<int\|string,scalar\|null>** |             |

***

### queryBuilder

```php
public queryBuilder(): \Qubus\Expressive\QueryBuilder
```

***

### getSchema

```php
public getSchema(): \Qubus\Expressive\Schema
```

***

### schemaCompiler

```php
public schemaCompiler(): \Qubus\Expressive\Schema\Compiler
```

***

### getDsn

```php
public getDsn(): ?string
```

***

### quoteIdentifier

```php
public quoteIdentifier(string $identifier): string
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$identifier` | **string** |             |

***

### listTables

```php
public listTables(): list<string>
```

***

### transactional

```php
public transactional(\Closure $callback): mixed
```

**Parameters:**

| Parameter   | Type         | Description |
|-------------|--------------|-------------|
| `$callback` | **\Closure** |             |

***

### supportsReturning

Driver feature detection.

```php
public supportsReturning(): bool
```

***

### supportsUpsert

```php
public supportsUpsert(): bool
```

***
