# BaseTask

***

* Full name: `\Codefy\Framework\Scheduler\BaseTask`
* Parent class: [`\Codefy\Framework\Scheduler\Processor\BaseProcessor`](./Processor/BaseProcessor.md)
* This class implements:
  [`\Codefy\Framework\Scheduler\Task`](./Task.md)
* This class is an **Abstract class**

## Properties

### pid

```php
protected ?\Codefy\Framework\Scheduler\ValueObject\TaskId $pid
```

***

### options

```php
protected (array|int|string|bool|\Cron\CronExpression|null)[] $options
```

***

### timeZone

```php
protected string|null $timeZone
```

***

### filters

```php
protected callable[]|\Closure[] $filters
```

***

### rejects

```php
protected callable[]|\Closure[] $rejects
```

***

### schedule

```php
protected ?\Codefy\Framework\Scheduler\Schedule $schedule
```

***

### dispatcher

```php
protected ?\Psr\EventDispatcher\EventDispatcherInterface $dispatcher
```

***

## Methods

### withOptions

Return an instance with configured options.

```php
public withOptions(array $options): self
```

**Parameters:**

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `$options` | **array** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### withScheduler

Return an instance with scheduler.

```php
public withScheduler(\Codefy\Framework\Scheduler\Schedule $schedule): self
```

**Parameters:**

| Parameter   | Type                                     | Description |
|-------------|------------------------------------------|-------------|
| `$schedule` | **\Codefy\Framework\Scheduler\Schedule** |             |

***

### withDispatcher

Return an instance with event dispatcher.

```php
public withDispatcher(\Psr\EventDispatcher\EventDispatcherInterface $dispatcher): self
```

**Parameters:**

| Parameter     | Type                                              | Description |
|---------------|---------------------------------------------------|-------------|
| `$dispatcher` | **\Psr\EventDispatcher\EventDispatcherInterface** |             |

***

### getOption

```php
public getOption(?string $option): mixed
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$option` | **?string** |             |

***

### pid

```php
public pid(): \Codefy\Framework\Scheduler\ValueObject\TaskId
```

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### setUp

Called before a task is executed.

```php
public setUp(): void
```

***

### execute

Executes a task.

```php
public execute(\Codefy\Framework\Scheduler\Schedule $schedule): void
```

* This method is **abstract**.
**Parameters:**

| Parameter   | Type                                     | Description |
|-------------|------------------------------------------|-------------|
| `$schedule` | **\Codefy\Framework\Scheduler\Schedule** |             |

***

### tearDown

Called after a task is executed.

```php
public tearDown(): void
```

***

### notYet

Check if time hasn't arrived.

```php
protected notYet(string $datetime): bool
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$datetime` | **string** |             |

***

### past

Check if the time has passed.

```php
protected past(string $datetime): bool
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$datetime` | **string** |             |

***

### from

Check if event should be run.

```php
public from(string $datetime): static
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$datetime` | **string** |             |

***

### to

Check if event should not run.

```php
public to(string $datetime): static
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$datetime` | **string** |             |

***

### shouldRun

Checks whether the task can and should run.

```php
private shouldRun(): bool
```

***

### run

```php
public run(): bool
```

***

## Inherited methods

### cron

The Cron expression representing the task's frequency.

```php
public cron(string $expression = '* * * * *'): self
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$expression` | **string** |             |

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

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$startTime` | **string** |             |
| `$endTime`   | **string** |             |

***

### unlessBetween

Schedule task that doesn't fall between start and end time.

```php
public unlessBetween(string $startTime, string $endTime): self
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$startTime` | **string** |             |
| `$endTime`   | **string** |             |

***

### inTimeInterval

Schedule task to run between start and end time.

```php
private inTimeInterval(string $startTime, string $endTime): \Closure
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$startTime` | **string** |             |
| `$endTime`   | **string** |             |

***

### hourly

Schedule the task to run hourly.

```php
public hourly(int|string $minute = 1): self
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$minute` | **int\|string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### daily

Schedule the task to run daily.

```php
public daily(?string $time = null): self
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$time`   | **?string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### on

Schedule the task to run on a certain date.

```php
public on(string $date): self
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$date`   | **string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### at

Schedule the command at a given time.

```php
public at(?string $time = null): self
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$time`   | **?string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### dailyAt

Schedule the task to run daily at a given time (10:00, 19:30, etc).

```php
public dailyAt(?string $time = null): self
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$time`   | **?string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### twiceDaily

Schedule the task to run twice daily.

```php
public twiceDaily(int $first = 1, int $second = 13): self
```

**Parameters:**

| Parameter | Type    | Description  |
|-----------|---------|--------------|
| `$first`  | **int** | First hour.  |
| `$second` | **int** | Second hour. |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### twiceDailyAt

Schedule the task to run twice daily at a given minute.

```php
public twiceDailyAt(int $first = 1, int $second = 13, int $minute = 0): self
```

**Parameters:**

| Parameter | Type    | Description  |
|-----------|---------|--------------|
| `$first`  | **int** | First hour.  |
| `$second` | **int** | Second hour. |
| `$minute` | **int** | Minute.      |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### weekdays

Schedule the task to run only on weekdays.

```php
public weekdays(?string $time = null): self
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$time`   | **?string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### weekends

Schedule the task to run only on weekdays.

```php
public weekends(?string $time = null): self
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$time`   | **?string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### mondays

Schedule the task to run only on Mondays.

```php
public mondays(?string $time = null): self
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$time`   | **?string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### tuesdays

Schedule the task to run only on Tuesdays.

```php
public tuesdays(?string $time = null): self
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$time`   | **?string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### wednesdays

Schedule the task to run only on Wednesdays.

```php
public wednesdays(?string $time = null): self
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$time`   | **?string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### thursdays

Schedule the task to run only on Thursdays.

```php
public thursdays(?string $time = null): self
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$time`   | **?string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### fridays

Schedule the task to run only on Fridays.

```php
public fridays(?string $time = null): self
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$time`   | **?string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### saturdays

Schedule the task to run only on Saturdays.

```php
public saturdays(?string $time = null): self
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$time`   | **?string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### sundays

Schedule the task to run only on Sundays.

```php
public sundays(?string $time = null): self
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$time`   | **?string** |             |

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
public weeklyOn(int|string $day, string $time = '0:0'): self
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$day`    | **int\|string** |             |
| `$time`   | **string**      |             |

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
public monthlyOn(int|string $dayOfMonth, string $time = '0:0'): self
```

**Parameters:**

| Parameter     | Type            | Description |
|---------------|-----------------|-------------|
| `$dayOfMonth` | **int\|string** |             |
| `$time`       | **string**      |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### lastDayOfTheMonth

Schedule the task to run monthly on a given day and time.

```php
public lastDayOfTheMonth(string $time = '0:0'): self
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$time`   | **string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### quarterly

Schedule the task to run quarterly.

```php
public quarterly(int|string|array $day = 1, ?string $time = null): self
```

**Parameters:**

| Parameter | Type                   | Description |
|-----------|------------------------|-------------|
| `$day`    | **int\|string\|array** |             |
| `$time`   | **?string**            |             |

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

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$month`  | **int**     |             |
| `$day`    | **int**     |             |
| `$time`   | **?string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### days

Set the days of the week the command should run on.

```php
public days(mixed $days): self
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$days`   | **mixed** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### hour

Set hour for the cron job.

```php
public hour(mixed $value): self
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### minute

Set minute for the cron job.

```php
public minute(mixed $value): self
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### dayOfMonth

Set day of the month for the cron job.

```php
public dayOfMonth(mixed $value): self
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### month

Set month for the cron job.

```php
public month(mixed $value): self
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### dayOfWeek

Set dah of the week for the cron job.

```php
public dayOfWeek(mixed $value): self
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### timezone

Set the timezone the date should be evaluated on.

```php
public timezone(\DateTimeZone|string $timezone): $this
```

**Parameters:**

| Parameter   | Type                      | Description |
|-------------|---------------------------|-------------|
| `$timezone` | **\DateTimeZone\|string** |             |

***

### every

Another way to the frequency of the cron job.

```php
public every(string|null $unit = null, float|int|null $value = null): self
```

**Parameters:**

| Parameter | Type                 | Description                           |
|-----------|----------------------|---------------------------------------|
| `$unit`   | **string\|null**     | (minute, hour, day, month or weekday) |
| `$value`  | **float\|int\|null** |                                       |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### everyMinute

Schedule task to run every minute of every $minute minutes.

```php
public everyMinute(string|int $minute = 1): self
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$minute` | **string\|int** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### everyHour

Schedule task to run every hour or every $hour hour and $minute minutes.

```php
public everyHour(string|int $hour = 1, int $minute = 0): self
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$hour`   | **string\|int** |             |
| `$minute` | **int**         |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### expressionPasses

Determine if the Cron expression passes.

```php
protected expressionPasses(string|\DateTimeZone|null $timezone = null): bool
```

**Parameters:**

| Parameter   | Type                            | Description |
|-------------|---------------------------------|-------------|
| `$timezone` | **string\|\DateTimeZone\|null** |             |

**Throws:**

- [`Exception`](../../../Exception.md)

***

### spliceIntoPosition

Splice the given value into the given position of the expression.

```php
protected spliceIntoPosition(int $position, string $value): self
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$position` | **int**    |             |
| `$value`    | **string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### setDayOfWeek

Internal function used by the everyMonday, etc functions.

```php
protected setDayOfWeek(int|string $day, ?string $time = null): self
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$day`    | **int\|string** |             |
| `$time`   | **?string**     |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### parseTime

Parses a time string (like 4:08 pm) into minutes and hours.

```php
protected parseTime(string $time): array
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$time`   | **string** |             |

***

### __construct

```php
public __construct(\Codefy\Framework\Scheduler\Mutex\Locker $mutex, callable|string $command, ?array $args = null, \DateTimeZone|string|null $timezone = null): mixed
```

**Parameters:**

| Parameter   | Type                                         | Description |
|-------------|----------------------------------------------|-------------|
| `$mutex`    | **\Codefy\Framework\Scheduler\Mutex\Locker** |             |
| `$command`  | **callable\|string**                         |             |
| `$args`     | **?array**                                   |             |
| `$timezone` | **\DateTimeZone\|string\|null**              |             |

***

### mutexName

Unique name to use for a mutually exclusive lock.

```php
public mutexName(): string
```

***

### withArgs

Set arguments for the command.

```php
public withArgs(array|null $args = null): static
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$args`   | **array\|null** |             |

***

### description

Set a command description.

```php
public description(string $description): static
```

**Parameters:**

| Parameter      | Type       | Description |
|----------------|------------|-------------|
| `$description` | **string** |             |

***

### runCommandInForeground

```php
protected runCommandInForeground(): string
```

***

### runCommandInBackground

```php
protected runCommandInBackground(): string
```

***

### runInForeground

Force the command to run in foreground.

```php
public runInForeground(): static
```

***

### canRunCommandInBackground

Check if the command can run in background.

```php
public canRunCommandInBackground(): bool
```

***

### callBeforeCallbacks

Call all the before callbacks for the command.

```php
public callBeforeCallbacks(): void
```

***

### callAfterCallbacks

Call all the after callbacks for the command.

```php
public callAfterCallbacks(): void
```

***

### when

Truth test to determine if a command should run when it is due.

```php
public when(callable|bool $callback): static
```

**Parameters:**

| Parameter   | Type               | Description |
|-------------|--------------------|-------------|
| `$callback` | **callable\|bool** |             |

***

### skip

Truth test to determine if a command should run when it is due.

```php
public skip(callable|bool $callback): static
```

**Parameters:**

| Parameter   | Type               | Description |
|-------------|--------------------|-------------|
| `$callback` | **callable\|bool** |             |

***

### before

Set a function to be called before a command is executed.

```php
public before(callable $fn): static
```

**Parameters:**

| Parameter | Type         | Description |
|-----------|--------------|-------------|
| `$fn`     | **callable** |             |

***

### after

Set a function to be called after a command is executed.

```php
public after(callable $fn): static
```

**Parameters:**

| Parameter | Type         | Description |
|-----------|--------------|-------------|
| `$fn`     | **callable** |             |

***

### then

Set a function to be called after a command is executed.

```php
public then(callable $fn, bool $runInBackground = false): static
```

**Parameters:**

| Parameter          | Type         | Description |
|--------------------|--------------|-------------|
| `$fn`              | **callable** |             |
| `$runInBackground` | **bool**     |             |

***

### onlyOneInstance

Prevents commands from overlapping.

```php
public onlyOneInstance(int $expiresAfter = 120): static
```

**Parameters:**

| Parameter       | Type    | Description                                               |
|-----------------|---------|-----------------------------------------------------------|
| `$expiresAfter` | **int** | The amount of time in seconds the mutex lock should live. |

***

### canRunOnlyOneInstance

Check if process con only have one instance.

```php
public canRunOnlyOneInstance(): bool
```

***

### maxRuntime

```php
public maxRuntime(): int
```

***

### getExpression

Gets the current cron expression for the task.

```php
public getExpression(): ?string
```

***

### isDue

Determine if the given command should run based on the Cron expression.

```php
public isDue(string|\DateTimeZone|null $timeZone = null): bool
```

**Parameters:**

| Parameter   | Type                            | Description |
|-------------|---------------------------------|-------------|
| `$timeZone` | **string\|\DateTimeZone\|null** |             |

**Throws:**

- [`Exception`](../../../Exception.md)

***

### compile

Compile the Task command.

```php
protected compile(): string
```

***

### getCommand

Returns the command.

```php
public getCommand(): callable|string
```

***

### sendEmail

Send email on Exception.

```php
public sendEmail(\Exception $ex): bool
```

**Parameters:**

| Parameter | Type           | Description |
|-----------|----------------|-------------|
| `$ex`     | **\Exception** |             |

***
