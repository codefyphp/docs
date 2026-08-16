# ResultSet

***

* Full name: `\Qubus\Expressive\ResultSet`

## Properties

### statement

```php
protected \PDOStatement $statement
```

***

## Methods

### __construct

Constructor

```php
public __construct(\PDOStatement $statement): mixed
```

**Parameters:**

| Parameter    | Type              | Description                                       |
|--------------|-------------------|---------------------------------------------------|
| `$statement` | **\PDOStatement** | The PDOStatement associated with this result set. |

***

### __destruct

Destructor

```php
public __destruct(): mixed
```

***

### count

Count affected rows

```php
public count(): int
```

***

### all

Fetch all results.

```php
public all(callable|null $callable = null, int $fetchStyle = 0): array|false
```

**Parameters:**

| Parameter     | Type               | Description                  |
|---------------|--------------------|------------------------------|
| `$callable`   | **callable\|null** | (optional) Callback function |
| `$fetchStyle` | **int**            | (optional) PDO fetch style   |

***

### allGroup

```php
public allGroup(bool $uniq = false, callable|null $callable = null): array|false
```

**Parameters:**

| Parameter   | Type               | Description |
|-------------|--------------------|-------------|
| `$uniq`     | **bool**           | (optional)  |
| `$callable` | **callable\|null** | (optional)  |

***

### first

Fetch first result

```php
public first(callable|null $callable = null): mixed
```

**Parameters:**

| Parameter   | Type               | Description                  |
|-------------|--------------------|------------------------------|
| `$callable` | **callable\|null** | (optional) Callback function |

***

### next

Fetch next result

```php
public next(): mixed
```

***

### flush

Close current cursor

```php
public flush(): bool
```

***

### column

Return a column

```php
public column(int $col = 0): mixed
```

**Parameters:**

| Parameter | Type    | Description                                         |
|-----------|---------|-----------------------------------------------------|
| `$col`    | **int** | 0-indexed number of the column you wish to retrieve |

***

### fetchAssoc

Fetch each result as an associative array

```php
public fetchAssoc(): $this
```

***

### fetchObject

Fetch each result as an stdClass object

```php
public fetchObject(): $this
```

***

### fetchNamed

```php
public fetchNamed(): $this
```

***

### fetchNum

```php
public fetchNum(): $this
```

***

### fetchBoth

```php
public fetchBoth(): $this
```

***

### fetchKeyPair

```php
public fetchKeyPair(): $this
```

***

### fetchClass

```php
public fetchClass(string $class, array $ctorargs = []): $this
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$class`    | **string** |             |
| `$ctorargs` | **array**  | (optional)  |

***

### fetchCustom

```php
public fetchCustom(\Closure $func): $this
```

**Parameters:**

| Parameter | Type         | Description |
|-----------|--------------|-------------|
| `$func`   | **\Closure** |             |

***
