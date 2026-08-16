# PdoDataMapper

***

* Full name: `\Qubus\Expressive\DataMapper\PdoDataMapper`
* This class implements:
  [`\Qubus\Expressive\DataMapper\DataMapper`](./DataMapper.md)

## Properties

### entity

```php
protected class-string<\Qubus\Expressive\DataMapper\SerializableEntity> $entity
```

***

### table

```php
protected string $table
```

***

### columns

```php
protected array<string,string> $columns
```

***

### properties

```php
private array<string,\ReflectionProperty> $properties
```

***

### connection

```php
public \Qubus\Expressive\Connection $connection
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Expressive\Connection $connection, string $entity): mixed
```

**Parameters:**

| Parameter     | Type                             | Description |
|---------------|----------------------------------|-------------|
| `$connection` | **\Qubus\Expressive\Connection** |             |
| `$entity`     | **string**                       |             |

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)
- [`DataMapperException`](./DataMapperException.md)

***

### getPdo

```php
public getPdo(): \PDO
```

***

### queryBuilder

```php
public queryBuilder(): \Qubus\Expressive\QueryBuilder
```

***

### hydrate

```php
public hydrate(list<array<string,mixed>> $data): array<int|string,\Qubus\Expressive\DataMapper\SerializableEntity>
```

**Parameters:**

| Parameter | Type                          | Description |
|-----------|-------------------------------|-------------|
| `$data`   | **list<array<string,mixed>>** |             |

**Throws:**

- [`DataMapperException`](./DataMapperException.md)

***

### findAll

```php
public findAll(string $orderBy = '', array{direction?: string, limit?: int, offset?: int} $options = []): array<int|string,\Qubus\Expressive\DataMapper\SerializableEntity>
```

**Parameters:**

| Parameter  | Type                                                     | Description |
|------------|----------------------------------------------------------|-------------|
| `$orderBy` | **string**                                               |             |
| `$options` | **array{direction?: string, limit?: int, offset?: int}** |             |

**Throws:**

- [`DataMapperException`](./DataMapperException.md)

***

### findAllBy

```php
public findAllBy(string $column, string $value, string $orderBy = '', array{direction?: string, limit?: int, offset?: int} $options = []): array<int|string,\Qubus\Expressive\DataMapper\SerializableEntity>
```

**Parameters:**

| Parameter  | Type                                                     | Description |
|------------|----------------------------------------------------------|-------------|
| `$column`  | **string**                                               |             |
| `$value`   | **string**                                               |             |
| `$orderBy` | **string**                                               |             |
| `$options` | **array{direction?: string, limit?: int, offset?: int}** |             |

**Throws:**

- [`DataMapperException`](./DataMapperException.md)

***

### findOne

```php
public findOne(int|string $id): \Qubus\Expressive\DataMapper\SerializableEntity|null
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$id`     | **int\|string** |             |

**Throws:**

- [`DataMapperException`](./DataMapperException.md)

***

### create

```php
public create(\Qubus\Expressive\DataMapper\SerializableEntity $entity): \Qubus\Expressive\DataMapper\SerializableEntity
```

**Parameters:**

| Parameter | Type                                                | Description |
|-----------|-----------------------------------------------------|-------------|
| `$entity` | **\Qubus\Expressive\DataMapper\SerializableEntity** |             |

**Throws:**

- [`DataMapperException`](./DataMapperException.md)

***

### update

```php
public update(\Qubus\Expressive\DataMapper\SerializableEntity $entity): \Qubus\Expressive\DataMapper\SerializableEntity
```

**Parameters:**

| Parameter | Type                                                | Description |
|-----------|-----------------------------------------------------|-------------|
| `$entity` | **\Qubus\Expressive\DataMapper\SerializableEntity** |             |

**Throws:**

- [`DataMapperException`](./DataMapperException.md)

***

### delete

```php
public delete(int|string $id): void
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$id`     | **int\|string** |             |

**Throws:**

- [`DataMapperException`](./DataMapperException.md)

***

### buildSelectString

```php
private buildSelectString(): string
```

**Throws:**

- [`DataMapperException`](./DataMapperException.md)

***

### buildOrderByString

```php
private buildOrderByString(string $orderBy, string $direction = 'ASC'): string
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$orderBy`   | **string** |             |
| `$direction` | **string** |             |

**Throws:**

- [`DataMapperException`](./DataMapperException.md)

***

### buildLimitOffsetString

```php
private buildLimitOffsetString(int $limit = 0, int $offset = 0): string
```

**Parameters:**

| Parameter | Type    | Description |
|-----------|---------|-------------|
| `$limit`  | **int** |             |
| `$offset` | **int** |             |

**Throws:**

- [`DataMapperException`](./DataMapperException.md)

***

### buildInsertString

```php
private buildInsertString(list<string> $properties): string
```

**Parameters:**

| Parameter     | Type             | Description |
|---------------|------------------|-------------|
| `$properties` | **list<string>** |             |

**Throws:**

- [`DataMapperException`](./DataMapperException.md)

***

### buildUpdateString

```php
private buildUpdateString(): string
```

**Throws:**

- [`DataMapperException`](./DataMapperException.md)

***

### buildDeleteString

```php
private buildDeleteString(): string
```

**Throws:**

- [`DataMapperException`](./DataMapperException.md)

***

### mapRowToObject

```php
private mapRowToObject(array<string,mixed> $row): \Qubus\Expressive\DataMapper\SerializableEntity
```

**Parameters:**

| Parameter | Type                    | Description |
|-----------|-------------------------|-------------|
| `$row`    | **array<string,mixed>** |             |

**Throws:**

- [`DataMapperException`](./DataMapperException.md)

***

### quotedColumn

```php
private quotedColumn(string $property): string
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$property` | **string** |             |

**Throws:**

- [`DataMapperException`](./DataMapperException.md)

***

### insertProperties

```php
private insertProperties(\Qubus\Expressive\DataMapper\SerializableEntity $entity): list<string>
```

**Parameters:**

| Parameter | Type                                                | Description |
|-----------|-----------------------------------------------------|-------------|
| `$entity` | **\Qubus\Expressive\DataMapper\SerializableEntity** |             |

***

### propertyValue

```php
private propertyValue(\Qubus\Expressive\DataMapper\SerializableEntity $entity, string $property): mixed
```

**Parameters:**

| Parameter   | Type                                                | Description |
|-------------|-----------------------------------------------------|-------------|
| `$entity`   | **\Qubus\Expressive\DataMapper\SerializableEntity** |             |
| `$property` | **string**                                          |             |

**Throws:**

- [`DataMapperException`](./DataMapperException.md)

***
