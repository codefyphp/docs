# Schedule

***

* Full name: `\Codefy\Framework\Scheduler\Schedule`

## Constants

| Constant    | Visibility | Type | Value |
|-------------|------------|------|-------|
| `SUNDAY`    | public     |      | 0     |
| `MONDAY`    | public     |      | 1     |
| `TUESDAY`   | public     |      | 2     |
| `WEDNESDAY` | public     |      | 3     |
| `THURSDAY`  | public     |      | 4     |
| `FRIDAY`    | public     |      | 5     |
| `SATURDAY`  | public     |      | 6     |

## Properties

### processors

```php
protected \Codefy\Framework\Scheduler\Processor\Processor[] $processors
```

***

### executedProcessors

```php
public \Codefy\Framework\Scheduler\Processor\Processor[] $executedProcessors
```

***

### failedProcessors

```php
public \Codefy\Framework\Scheduler\FailedProcessor[] $failedProcessors
```

***

### dispatcher

```php
public \Psr\EventDispatcher\EventDispatcherInterface $dispatcher
```

***

### timeZone

```php
public \Qubus\Support\DateTime\QubusDateTimeZone $timeZone
```

***

### mutex

```php
public \Codefy\Framework\Scheduler\Mutex\Locker $mutex
```

***

## Methods

### __construct

```php
public __construct(\Psr\EventDispatcher\EventDispatcherInterface $dispatcher, \Qubus\Support\DateTime\QubusDateTimeZone $timeZone, \Codefy\Framework\Scheduler\Mutex\Locker $mutex): mixed
```

**Parameters:**

| Parameter     | Type                                              | Description |
|---------------|---------------------------------------------------|-------------|
| `$dispatcher` | **\Psr\EventDispatcher\EventDispatcherInterface** |             |
| `$timeZone`   | **\Qubus\Support\DateTime\QubusDateTimeZone**     |             |
| `$mutex`      | **\Codefy\Framework\Scheduler\Mutex\Locker**      |             |

***

### queueProcessor

Add a single Processor to the stack.

```php
public queueProcessor(\Codefy\Framework\Scheduler\Processor\Processor $processor): self
```

**Parameters:**

| Parameter    | Type                                                | Description |
|--------------|-----------------------------------------------------|-------------|
| `$processor` | **\Codefy\Framework\Scheduler\Processor\Processor** |             |

***

### command

```php
public command(callable|string $command, array $args = []): \Codefy\Framework\Scheduler\Processor\Shell|\Codefy\Framework\Scheduler\Processor\Callback
```

**Parameters:**

| Parameter  | Type                 | Description |
|------------|----------------------|-------------|
| `$command` | **callable\|string** |             |
| `$args`    | **array**            |             |

***

### php

```php
public php(string $script, ?string $bin = null, array $args = []): \Codefy\Framework\Scheduler\Processor\Shell
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$script` | **string**  |             |
| `$bin`    | **?string** |             |
| `$args`   | **array**   |             |

***

### task

```php
public task(class-string $task, array $options = []): \Codefy\Framework\Scheduler\Task
```

**Parameters:**

| Parameter  | Type             | Description |
|------------|------------------|-------------|
| `$task`    | **class-string** |             |
| `$options` | **array**        |             |

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)
- [`Exception`](../../../Exception.md)

***

### allProcessors

```php
public allProcessors(): \Codefy\Framework\Scheduler\Processor\Processor[]
```

***

### dueProcessors

Get all the processors on the schedule that are due.

```php
public dueProcessors(): \Codefy\Framework\Scheduler\Processor\Processor[]
```

***

### run

```php
public run(): void
```

***

### resetRun

Reset all collected data of last run.

```php
public resetRun(): static
```

Call before run() if you call run() multiple times.

***

### pushExecutedProcessor

Push a successfully executed process.

```php
private pushExecutedProcessor(\Codefy\Framework\Scheduler\Processor\Processor $processor): \Codefy\Framework\Scheduler\Processor\Processor
```

**Parameters:**

| Parameter    | Type                                                | Description |
|--------------|-----------------------------------------------------|-------------|
| `$processor` | **\Codefy\Framework\Scheduler\Processor\Processor** |             |

***

### pushFailedProcessor

Push a failed process.

```php
private pushFailedProcessor(\Codefy\Framework\Scheduler\Processor\Processor $processor, \Qubus\Exception\Exception $ex): \Codefy\Framework\Scheduler\Processor\Processor
```

**Parameters:**

| Parameter    | Type                                                | Description |
|--------------|-----------------------------------------------------|-------------|
| `$processor` | **\Codefy\Framework\Scheduler\Processor\Processor** |             |
| `$ex`        | **\Qubus\Exception\Exception**                      |             |

***

### compileArguments

Compile the Task command.

```php
protected compileArguments(array $args = []): string
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$args`   | **array** |             |

***

## Inherited methods

### alias

```php
public alias(?string $literal): \Cron\CronExpression
```

**Parameters:**

| Parameter  | Type        | Description |
|------------|-------------|-------------|
| `$literal` | **?string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***
