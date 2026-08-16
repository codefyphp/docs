# CreateColumn

***

* Full name: `\Qubus\Expressive\Schema\CreateColumn`
* Parent class: [`\Qubus\Expressive\Schema\BaseColumn`](./BaseColumn.md)

## Properties

### table

```php
protected ?\Qubus\Expressive\Schema\CreateTable $table
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Expressive\Schema\CreateTable $table, string $name, string $type): mixed
```

**Parameters:**

| Parameter | Type                                     | Description |
|-----------|------------------------------------------|-------------|
| `$table`  | **\Qubus\Expressive\Schema\CreateTable** |             |
| `$name`   | **string**                               |             |
| `$type`   | **string**                               |             |

***

### getTable

```php
public getTable(): \Qubus\Expressive\Schema\CreateTable
```

***

### autoincrement

```php
public autoincrement(?string $name = null): $this
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$name`   | **?string** |             |

***

### primary

```php
public primary(?string $name = null): $this
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$name`   | **?string** |             |

***

### unique

```php
public unique(?string $name = null): $this
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$name`   | **?string** |             |

***

### index

```php
public index(?string $name = null): $this
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$name`   | **?string** |             |

***

## Inherited methods

### __construct

```php
public __construct(string $name, ?string $type = null): mixed
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$name`   | **string**  |             |
| `$type`   | **?string** |             |

***

### getName

```php
public getName(): string
```

***

### getType

```php
public getType(): string
```

***

### getProperties

```php
public getProperties(): array
```

***

### setType

```php
public setType(string $type): $this
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$type`   | **string** |             |

***

### set

```php
public set(string $name, mixed $value): $this
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |
| `$value`  | **mixed**  |             |

***

### has

```php
public has(string $name): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### get

```php
public get(string $name, mixed|null $default = null): mixed|null
```

**Parameters:**

| Parameter  | Type            | Description |
|------------|-----------------|-------------|
| `$name`    | **string**      |             |
| `$default` | **mixed\|null** |             |

***

### size

```php
public size(string $value): $this
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$value`  | **string** |             |

***

### notNull

```php
public notNull(): $this
```

***

### description

```php
public description(string $comment): $this
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$comment` | **string** |             |

***

### defaultValue

```php
public defaultValue(mixed $value): $this
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### unsigned

```php
public unsigned(bool $value = true): $this
```

**Parameters:**

| Parameter | Type     | Description |
|-----------|----------|-------------|
| `$value`  | **bool** |             |

***

### length

```php
public length(mixed $value): $this
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***
