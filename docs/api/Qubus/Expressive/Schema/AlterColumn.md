# AlterColumn

***

* Full name: `\Qubus\Expressive\Schema\AlterColumn`
* Parent class: [`\Qubus\Expressive\Schema\BaseColumn`](./BaseColumn.md)

## Properties

### table

```php
protected string|\Qubus\Expressive\Schema\AlterTable|null $table
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Expressive\Schema\AlterTable $table, string $name, ?string $type = null): mixed
```

**Parameters:**

| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| `$table`  | **\Qubus\Expressive\Schema\AlterTable** |             |
| `$name`   | **string**                              |             |
| `$type`   | **?string**                             |             |

***

### getTable

```php
public getTable(): string
```

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

### autoincrement

```php
public autoincrement(): $this
```

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
