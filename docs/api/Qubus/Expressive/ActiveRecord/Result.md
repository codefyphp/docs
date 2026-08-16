# Result

***

* Full name: `\Qubus\Expressive\ActiveRecord\Result`
* This class implements:
  `Countable`,
  `IteratorAggregate`

## Properties

### model

```php
protected ?\Qubus\Expressive\ActiveRecord\Model $model
```

***

### query

```php
protected \Qubus\Expressive\QueryBuilder|false|null $query
```

***

### rows

```php
protected array $rows
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Expressive\ActiveRecord\Model $model, \Qubus\Expressive\QueryBuilder|false|null $query = null): mixed
```

**Parameters:**

| Parameter | Type                                            | Description |
|-----------|-------------------------------------------------|-------------|
| `$model`  | **\Qubus\Expressive\ActiveRecord\Model**        |             |
| `$query`  | **\Qubus\Expressive\QueryBuilder\|false\|null** |             |

***

### row

```php
public row(): ?\Qubus\Expressive\ActiveRecord\Row
```

***

### rows

```php
public rows(): static
```

***

### first

```php
public first(): ?\Qubus\Expressive\ActiveRecord\Row
```

***

### pluck

```php
public pluck(mixed $field): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$field`  | **mixed** |             |

***

### load

```php
public load(mixed $method): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$method` | **mixed** |             |

***

### toArray

```php
public toArray(): array
```

***

### toJson

```php
public toJson(): bool|string
```

***

### getIterator

```php
public getIterator(): \ArrayIterator
```

***

### count

```php
public count(): int
```

***
