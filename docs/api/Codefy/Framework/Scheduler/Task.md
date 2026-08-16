# Task

***

* Full name: `\Codefy\Framework\Scheduler\Task`
* Parent interfaces:
  [`\Codefy\Framework\Scheduler\Processor\Processor`](./Processor/Processor.md)

## Methods

### withOptions

Return an instance with configured options.

```php
public withOptions((array|int|string|bool|\Cron\CronExpression|null)[] $options): self
```

**Parameters:**

| Parameter  | Type                                                         | Description |
|------------|--------------------------------------------------------------|-------------|
| `$options` | **(array\|int\|string\|bool\|\Cron\CronExpression\|null)[]** |             |

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

## Inherited methods

### mutexName

Unique name to use for a mutually exclusive lock.

```php
public mutexName(): string
```

***

### maxRuntime

```php
public maxRuntime(): int
```

***

### description

Set a command description.

```php
public description(string $description): self
```

**Parameters:**

| Parameter      | Type       | Description |
|----------------|------------|-------------|
| `$description` | **string** |             |

***

### canRunCommandInBackground

Check if the command can run in background.

```php
public canRunCommandInBackground(): bool
```

***

### canRunOnlyOneInstance

Check if process con only have one instance.

```php
public canRunOnlyOneInstance(): bool
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

***

### run

```php
public run(): mixed
```

***

### getCommand

Returns the command.

```php
public getCommand(): callable|string
```

***
