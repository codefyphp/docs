# EveryMinute

***

* Full name: `\Codefy\Framework\Scheduler\Expressions\EveryMinute`
* This class is marked as **final** and can't be subclassed
* This class implements:
  [`\Codefy\Framework\Scheduler\Expressions\Expressional`](./Expressional.md)
* This class is a **Final class**

## Methods

### make

Set the job execution time to every minute.

```php
public static make(int|string|array|null $minute = null): \Cron\CronExpression
```

* This method is **static**.
**Parameters:**

| Parameter | Type                         | Description                                                         |
|-----------|------------------------------|---------------------------------------------------------------------|
| `$minute` | **int\|string\|array\|null** | If not null, specifies that the job will run every $minute minutes. |

**Throws:**

- [`TypeException`](../../../../Qubus/Exception/Data/TypeException.md)

***

## Inherited methods

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
