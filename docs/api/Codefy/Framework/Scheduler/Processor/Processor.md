# Processor

***

* Full name: `\Codefy\Framework\Scheduler\Processor\Processor`

## Methods

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
