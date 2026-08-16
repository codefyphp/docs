# February

***

* Full name: `\Codefy\Framework\Scheduler\Expressions\MonthOfYear\February`
* This class is marked as **final** and can't be subclassed
* This class implements:
  [`\Codefy\Framework\Scheduler\Expressions\Expressional`](../Expressional.md)
* This class is a **Final class**

## Methods

### make

Sets the job execution time to run once every February.

```php
public static make(int|string|array $day = 1, int|string|array $hour = 0, int|string|array $minute = 0): \Cron\CronExpression
```

* This method is **static**.
**Parameters:**

| Parameter | Type                   | Description |
|-----------|------------------------|-------------|
| `$day`    | **int\|string\|array** |             |
| `$hour`   | **int\|string\|array** |             |
| `$minute` | **int\|string\|array** |             |

**Throws:**

- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)

***
