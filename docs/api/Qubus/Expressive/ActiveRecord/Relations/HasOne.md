# HasOne

***

* Full name: `\Qubus\Expressive\ActiveRecord\Relations\HasOne`
* Parent class: [`\Qubus\Expressive\ActiveRecord\Relations\Relation`](./Relation.md)

## Properties

### foreignKey

```php
protected int|string|null $foreignKey
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Expressive\ActiveRecord\Model $parent, \Qubus\Expressive\ActiveRecord\Model $related, string|int|null $foreignKey = null): mixed
```

**Parameters:**

| Parameter     | Type                                     | Description |
|---------------|------------------------------------------|-------------|
| `$parent`     | **\Qubus\Expressive\ActiveRecord\Model** |             |
| `$related`    | **\Qubus\Expressive\ActiveRecord\Model** |             |
| `$foreignKey` | **string\|int\|null**                    |             |

***

### setJoin

```php
public setJoin(): mixed
```

***

### match

```php
public match(\Qubus\Expressive\ActiveRecord\Model $parent): mixed
```

**Parameters:**

| Parameter | Type                                     | Description |
|-----------|------------------------------------------|-------------|
| `$parent` | **\Qubus\Expressive\ActiveRecord\Model** |             |

***

### getResults

```php
public getResults(): mixed
```

***

## Inherited methods

### __construct

```php
public __construct(\Qubus\Expressive\ActiveRecord\Model $parent, \Qubus\Expressive\ActiveRecord\Model $related): mixed
```

**Parameters:**

| Parameter  | Type                                     | Description |
|------------|------------------------------------------|-------------|
| `$parent`  | **\Qubus\Expressive\ActiveRecord\Model** |             |
| `$related` | **\Qubus\Expressive\ActiveRecord\Model** |             |

***

### getResults

```php
public getResults(): mixed
```

* This method is **abstract**.
***

### setJoin

```php
public setJoin(): mixed
```

* This method is **abstract**.
***

### match

```php
public match(\Qubus\Expressive\ActiveRecord\Model $parent): mixed
```

* This method is **abstract**.
**Parameters:**

| Parameter | Type                                     | Description |
|-----------|------------------------------------------|-------------|
| `$parent` | **\Qubus\Expressive\ActiveRecord\Model** |             |

***

### eagerLoad

```php
public eagerLoad(mixed $parentRows, mixed $relatedKeys, mixed $relation): mixed
```

**Parameters:**

| Parameter      | Type      | Description |
|----------------|-----------|-------------|
| `$parentRows`  | **mixed** |             |
| `$relatedKeys` | **mixed** |             |
| `$relation`    | **mixed** |             |

***

### relate

```php
public relate(\Qubus\Expressive\ActiveRecord\Model $parent): mixed
```

**Parameters:**

| Parameter | Type                                     | Description |
|-----------|------------------------------------------|-------------|
| `$parent` | **\Qubus\Expressive\ActiveRecord\Model** |             |

***

### getIterator

```php
public getIterator(): \Qubus\Expressive\ActiveRecord\Result|\Iterator
```

***

### count

```php
public count(): int
```

***

### __call

```php
public __call(mixed $name, mixed $param): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$name`   | **mixed** |             |
| `$param`  | **mixed** |             |

***
