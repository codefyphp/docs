# Select

***

* Full name: `\Qubus\Expressive\Select`

## Constants


| Constant       | Visibility | Type | Value   |
|----------------|------------|------|---------|
| `OPERATOR_AND` | public     |      | ' AND ' |
| `OPERATOR_OR`  | public     |      | ' OR '  |

## Methods

### query

To execute a raw query

```php
public query(string $query, array<int|string,mixed> $parameters = [], bool $returnAsPdoStmt = false): \Qubus\Expressive\Database|\PDOStatement
```

**Parameters:**

| Parameter          | Type                         | Description                                                                                                                                |
|--------------------|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| `$query`           | **string**                   |                                                                                                                                            |
| `$parameters`      | **array<int\|string,mixed>** |                                                                                                                                            |
| `$returnAsPdoStmt` | **bool**                     | True, it will return the PDOStatement
false, it will return $this, which can be used for chaining
or access the properties of the results. |

***

### find

To find all rows and create their instances
Use the query builder to build the where clause or $this->query with select
If a callback function is provided, the 1st arg must accept the rows results

```php
public find(callable|null $callback = null): mixed
```

$this->find(function($rows){
  // do more stuff here...
});

**Parameters:**

| Parameter   | Type               | Description                         |
|-------------|--------------------|-------------------------------------|
| `$callback` | **callable\|null** | Run a function on the returned rows |

**Return Value:**

The callback result, an iterator of rows, or false when no statement was executed.

***

### findOne

Return one row

```php
public findOne(int|string|null $id = null): \Qubus\Expressive\Database|false
```

**Parameters:**

| Parameter | Type                  | Description                  |
|-----------|-----------------------|------------------------------|
| `$id`     | **int\|string\|null** | Use to fetch by primary key. |

***

### select

Create the select clause.

```php
public select(mixed $columns = '*', string|null $alias = null): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter  | Type             | Description                                                |
|------------|------------------|------------------------------------------------------------|
| `$columns` | **mixed**        | The column(s) to select. Can be string or array of fields. |
| `$alias`   | **string\|null** | An alias to the column.                                    |

***

### getSelectFields

Return the select fields as array.

```php
public getSelectFields(): list<string>
```

***

### fromArray

Create an instance from the given row (an associative
array of data fetched from the database).

```php
public fromArray(array<string,mixed> $data): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter | Type                    | Description |
|-----------|-------------------------|-------------|
| `$data`   | **array<string,mixed>** |             |

***

### having

```php
public having(mixed $statement, string $operator = \self::OPERATOR_AND): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$statement` | **mixed**  |             |
| `$operator`  | **string** |             |

***

### groupBy

GROUP BY $columnName

```php
public groupBy(string $columnName): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$columnName` | **string** |             |

***
