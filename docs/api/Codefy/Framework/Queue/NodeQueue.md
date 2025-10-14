***

# NodeQueue





* Full name: `\Codefy\Framework\Queue\NodeQueue`
* This class implements:
[`\Codefy\Framework\Queue\ReliableQueue`](./ReliableQueue.md), [`\Codefy\Framework\Queue\QueueGarbageCollection`](./QueueGarbageCollection.md)



## Properties


### queue



```php
protected ?\Codefy\Framework\Queue\ShouldQueue $queue
```






***

### db



```php
private ?\Qubus\NoSql\Collection $db
```






***

## Methods


### __construct



```php
public __construct(\Codefy\Framework\Queue\ShouldQueue $queue, ?string $node = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$queue` | **\Codefy\Framework\Queue\ShouldQueue** |  |
| `$node` | **?string** |  |





***

### isDue



```php
public isDue(string|callable $schedule): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$schedule` | **string&#124;callable** |  |





***

### createItem

Adds a queue item and store it directly to the queue.

```php
public createItem(): string
```









**Return Value:**

A unique ID if the item was successfully created and was (best effort)
added to the queue, otherwise FALSE. We don't guarantee the item was
committed to disk etc, but as far as we know, the item is now in the
queue.




***

### doCreateItem

Adds a queue item and store it directly to the queue.

```php
protected doCreateItem(): string
```









**Return Value:**

A unique ID if the item was successfully created and was (best effort)
added to the queue, otherwise false. We don't guarantee the item was
committed to disk etc, but as far as we know, the item is now in the
queue.



**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

- [`ReflectionException`](../../../ReflectionException.md)



***

### numberOfItems

Retrieves the number of items in the queue.

```php
public numberOfItems(): int
```









**Return Value:**

An integer estimate of the number of items in the queue.




***

### claimItem

Claims an item in the queue for processing.

```php
public claimItem(int $leaseTime = 3600): array|object|bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$leaseTime` | **int** | How long the processing is expected to take in seconds,<br />defaults to an hour. After this lease expires, the item<br />will be reset and another consumer can claim the item.<br />For idempotent tasks (which can be run multiple times<br />without side effects), shorter lease times would result<br />in lower latency in case a consumer fails. For tasks<br />that should not be run more than once (non-idempotent),<br />a larger lease time will make it more rare for a given<br />task to run multiple times in cases of failure, at the<br />cost of higher latency. |


**Return Value:**

On success, we return an item object|array. If the queue is
                  unable to claim an item it returns false. This implies
                  a best effort to retrieve an item and either the queue
                  is empty or there is some other non-recoverable problem.

If returned, the object|array will have at least the following properties:
- data: the same as what was passed into createItem().
- _id: the unique ID returned from createItem().
- created: timestamp when the item was put into the queue.




***

### deleteItem

Deletes a finished item from the queue.

```php
public deleteItem(mixed $item): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$item` | **mixed** | The item returned by claimItem(). |





***

### releaseItem

Releases an item that the worker could not process.

```php
public releaseItem(mixed $item): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$item` | **mixed** | The item returned by claimItem(). |


**Return Value:**

TRUE if the item has been released, FALSE otherwise.




***

### createQueue

Creates a queue.

```php
public createQueue(): mixed
```












***

### deleteQueue

Deletes a queue and every item in the queue.

```php
public deleteQueue(): void
```












***

### garbageCollection

Cleans queues of garbage.

```php
public garbageCollection(): void
```











**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### catchException

Act on an exception when queue might be stale.

```php
protected catchException(\Exception $e): void
```

If the node does not yet exist, that's fine, but if the node exists and
yet the query failed, then the queue is stale and the exception needs to
propagate.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$e` | **\Exception** | The exception. |




**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### dispatch



```php
public dispatch(): bool
```











**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***


## Inherited methods


### cron

The Cron expression representing the task's frequency.

```php
public cron(string $expression = &#039;* * * * *&#039;): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$expression` | **string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### filtersPass

Determine if the filters pass.

```php
public filtersPass(): bool
```












***

### between

Schedule task to run between start and end time.

```php
public between(string $startTime, string $endTime): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$startTime` | **string** |  |
| `$endTime` | **string** |  |





***

### unlessBetween

Schedule task that doesn't fall between start and end time.

```php
public unlessBetween(string $startTime, string $endTime): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$startTime` | **string** |  |
| `$endTime` | **string** |  |





***

### inTimeInterval

Schedule task to run between start and end time.

```php
private inTimeInterval(string $startTime, string $endTime): \Closure
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$startTime` | **string** |  |
| `$endTime` | **string** |  |





***

### hourly

Schedule the task to run hourly.

```php
public hourly(int|string $minute = 1): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$minute` | **int&#124;string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### daily

Schedule the task to run daily.

```php
public daily(?string $time = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **?string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### on

Schedule the task to run on a certain date.

```php
public on(string $date): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$date` | **string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### at

Schedule the command at a given time.

```php
public at(?string $time = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **?string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### dailyAt

Schedule the task to run daily at a given time (10:00, 19:30, etc).

```php
public dailyAt(?string $time = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **?string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### twiceDaily

Schedule the task to run twice daily.

```php
public twiceDaily(int $first = 1, int $second = 13): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$first` | **int** | First hour. |
| `$second` | **int** | Second hour. |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### twiceDailyAt

Schedule the task to run twice daily at a given minute.

```php
public twiceDailyAt(int $first = 1, int $second = 13, int $minute): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$first` | **int** | First hour. |
| `$second` | **int** | Second hour. |
| `$minute` | **int** | Minute. |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### weekdays

Schedule the task to run only on weekdays.

```php
public weekdays(?string $time = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **?string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### weekends

Schedule the task to run only on weekdays.

```php
public weekends(?string $time = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **?string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### mondays

Schedule the task to run only on Mondays.

```php
public mondays(?string $time = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **?string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### tuesdays

Schedule the task to run only on Tuesdays.

```php
public tuesdays(?string $time = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **?string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### wednesdays

Schedule the task to run only on Wednesdays.

```php
public wednesdays(?string $time = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **?string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### thursdays

Schedule the task to run only on Thursdays.

```php
public thursdays(?string $time = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **?string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### fridays

Schedule the task to run only on Fridays.

```php
public fridays(?string $time = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **?string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### saturdays

Schedule the task to run only on Saturdays.

```php
public saturdays(?string $time = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **?string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### sundays

Schedule the task to run only on Sundays.

```php
public sundays(?string $time = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **?string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### weekly

Schedule the task to run weekly.

```php
public weekly(): self
```











**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### weeklyOn

Schedule the task to run weekly on a given day and time.

```php
public weeklyOn(int|string $day, string $time = &#039;0:0&#039;): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$day` | **int&#124;string** |  |
| `$time` | **string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### monthly

Schedule the task to run monthly.

```php
public monthly(): self
```











**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### monthlyOn

Schedule the task to run monthly on a given day and time.

```php
public monthlyOn(int|string $dayOfMonth, string $time = &#039;0:0&#039;): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$dayOfMonth` | **int&#124;string** |  |
| `$time` | **string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### lastDayOfTheMonth

Schedule the task to run monthly on a given day and time.

```php
public lastDayOfTheMonth(string $time = &#039;0:0&#039;): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### quarterly

Schedule the task to run quarterly.

```php
public quarterly(int|string|array $day = 1, ?string $time = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$day` | **int&#124;string&#124;array** |  |
| `$time` | **?string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### yearly

Schedule the task to run yearly.

```php
public yearly(): self
```











**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### yearlyOn

Schedule the task to run yearly.

```php
public yearlyOn(int $month, int $day, ?string $time = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$month` | **int** |  |
| `$day` | **int** |  |
| `$time` | **?string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### days

Set the days of the week the command should run on.

```php
public days(mixed $days): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$days` | **mixed** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### hour

Set hour for the cron job.

```php
public hour(mixed $value): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **mixed** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### minute

Set minute for the cron job.

```php
public minute(mixed $value): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **mixed** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### dayOfMonth

Set day of the month for the cron job.

```php
public dayOfMonth(mixed $value): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **mixed** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### month

Set month for the cron job.

```php
public month(mixed $value): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **mixed** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### dayOfWeek

Set dah of the week for the cron job.

```php
public dayOfWeek(mixed $value): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **mixed** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### timezone

Set the timezone the date should be evaluated on.

```php
public timezone(\DateTimeZone|string $timezone): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$timezone` | **\DateTimeZone&#124;string** |  |





***

### every

Another way to the frequency of the cron job.

```php
public every(string|null $unit = null, float|int|null $value = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$unit` | **string&#124;null** | (minute, hour, day, month or weekday) |
| `$value` | **float&#124;int&#124;null** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### everyMinute

Schedule task to run every minute of every $minute minutes.

```php
public everyMinute(string|int $minute = 1): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$minute` | **string&#124;int** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### everyHour

Schedule task to run every hour or every $hour hour and $minute minutes.

```php
public everyHour(string|int $hour = 1, int $minute): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$hour` | **string&#124;int** |  |
| `$minute` | **int** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### expressionPasses

Determine if the Cron expression passes.

```php
protected expressionPasses(string|\DateTimeZone|null $timezone = null): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$timezone` | **string&#124;\DateTimeZone&#124;null** |  |




**Throws:**

- [`Exception`](../../../Exception.md)



***

### spliceIntoPosition

Splice the given value into the given position of the expression.

```php
protected spliceIntoPosition(int $position, string $value): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$position` | **int** |  |
| `$value` | **string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### setDayOfWeek

Internal function used by the everyMonday, etc functions.

```php
protected setDayOfWeek(int|string $day, ?string $time = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$day` | **int&#124;string** |  |
| `$time` | **?string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### parseTime

Parses a time string (like 4:08 pm) into minutes and hours.

```php
protected parseTime(string $time): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$time` | **string** |  |





***


***
> Automatically generated on 2025-10-13
