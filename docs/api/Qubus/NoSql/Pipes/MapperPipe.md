# MapperPipe

***

* Full name: `\Qubus\NoSql\Pipes\MapperPipe`
* This class implements:
  [`\Qubus\NoSql\Pipes\Pipe`](./Pipe.md)

## Properties

### mappers

```php
protected array $mappers
```

***

## Methods

### process

```php
public process(array $data): array
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **array** |             |

***

### add

```php
public add(\Closure $mapper): void
```

**Parameters:**

| Parameter | Type         | Description |
|-----------|--------------|-------------|
| `$mapper` | **\Closure** |             |

***
