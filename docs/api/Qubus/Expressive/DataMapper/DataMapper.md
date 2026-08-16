# DataMapper

***

* Full name: `\Qubus\Expressive\DataMapper\DataMapper`

## Methods

### findAll

```php
public findAll(string $orderBy = '', array{direction?: string, limit?: int, offset?: int} $options = []): array<int|string,\Qubus\Expressive\DataMapper\SerializableEntity>
```

**Parameters:**

| Parameter  | Type                                                     | Description |
|------------|----------------------------------------------------------|-------------|
| `$orderBy` | **string**                                               |             |
| `$options` | **array{direction?: string, limit?: int, offset?: int}** |             |

***

### findOne

```php
public findOne(int|string $id): ?\Qubus\Expressive\DataMapper\SerializableEntity
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$id`     | **int\|string** |             |

***

### create

```php
public create(\Qubus\Expressive\DataMapper\SerializableEntity $entity): \Qubus\Expressive\DataMapper\SerializableEntity
```

**Parameters:**

| Parameter | Type                                                | Description |
|-----------|-----------------------------------------------------|-------------|
| `$entity` | **\Qubus\Expressive\DataMapper\SerializableEntity** |             |

***

### update

```php
public update(\Qubus\Expressive\DataMapper\SerializableEntity $entity): \Qubus\Expressive\DataMapper\SerializableEntity
```

**Parameters:**

| Parameter | Type                                                | Description |
|-----------|-----------------------------------------------------|-------------|
| `$entity` | **\Qubus\Expressive\DataMapper\SerializableEntity** |             |

***

### delete

```php
public delete(int|string $id): void
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$id`     | **int\|string** |             |

***
