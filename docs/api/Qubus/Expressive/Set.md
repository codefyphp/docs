# Set

***

* Full name: `\Qubus\Expressive\Set`

## Methods

### set

To set data for update or insert
$key can be an array for mass set

```php
public set(mixed $key, mixed|null $value = null): \Qubus\Expressive\Database
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$key`    | **mixed**       |             |
| `$value`  | **mixed\|null** |             |

***

### save

Save, a shortcut to update() or insert().

```php
public save(): \Qubus\Expressive\Database|int|bool
```

***
