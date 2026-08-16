# ScheduleValidateAware

***

* Full name: `\Codefy\Framework\Scheduler\Traits\ScheduleValidateAware`

## Methods

### sequence

```php
protected static sequence(int|string|array|null $minute = null, int|string|array|null $hour = null, int|string|array|null $day = null, int|string|array|null $month = null, int|string|array|null $weekday = null): array
```

* This method is **static**.
**Parameters:**

| Parameter  | Type                         | Description |
|------------|------------------------------|-------------|
| `$minute`  | **int\|string\|array\|null** |             |
| `$hour`    | **int\|string\|array\|null** |             |
| `$day`     | **int\|string\|array\|null** |             |
| `$month`   | **int\|string\|array\|null** |             |
| `$weekday` | **int\|string\|array\|null** |             |

**Throws:**

- [`TypeException`](../../../../Qubus/Exception/Data/TypeException.md)

***
### range

```php
protected static range(int|string|array|null $value = null, int $min = 0, int $max = 0): int|string|null
```

* This method is **static**.
**Parameters:**

| Parameter | Type                         | Description |
|-----------|------------------------------|-------------|
| `$value`  | **int\|string\|array\|null** |             |
| `$min`    | **int**                      |             |
| `$max`    | **int**                      |             |

**Throws:**

- [`TypeException`](../../../../Qubus/Exception/Data/TypeException.md)

***
