# SorterPipe

***

* Full name: `\Qubus\NoSql\Pipes\SorterPipe`
* This class implements:
  [`\Qubus\NoSql\Pipes\Pipe`](./Pipe.md)

## Properties

### value

```php
protected \Closure $value
```

***

### ascending

```php
protected string $ascending
```

***

## Methods

### __construct

```php
public __construct(\Closure $value, string $ascending = 'asc'): mixed
```

**Parameters:**

| Parameter    | Type         | Description |
|--------------|--------------|-------------|
| `$value`     | **\Closure** |             |
| `$ascending` | **string**   |             |

***

### process

```php
public process(array $data): array
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **array** |             |

***

### sort

```php
public sort(array $array, \Closure $value, string $ascending): array
```

**Parameters:**

| Parameter    | Type         | Description |
|--------------|--------------|-------------|
| `$array`     | **array**    |             |
| `$value`     | **\Closure** |             |
| `$ascending` | **string**   |             |

***
