***

# ConsoleKernel





* Full name: `\Codefy\Framework\Console\ConsoleKernel`
* This class implements:
[`\Codefy\Framework\Contracts\Console\Kernel`](../Contracts/Console/Kernel.md)



## Properties


### codex



```php
protected ?\Codefy\Framework\Console\ConsoleApplication $codex
```






***

### commands



```php
protected array $commands
```






***

### commandsLoaded



```php
protected bool $commandsLoaded
```






***

### schedule



```php
protected ?\Codefy\Framework\Scheduler\Schedule $schedule
```






***

### bootstrappers



```php
protected array $bootstrappers
```






***

### codefy



```php
protected \Codefy\Framework\Application $codefy
```






***

## Methods


### __construct



```php
public __construct(\Codefy\Framework\Application $codefy): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$codefy` | **\Codefy\Framework\Application** |  |





***

### defineConsoleSchedule



```php
protected defineConsoleSchedule(): void
```












***

### handle

Handle an incoming console command.

```php
public handle(\Symfony\Component\Console\Input\InputInterface $input, ?\Symfony\Component\Console\Output\OutputInterface $output = null): int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$input` | **\Symfony\Component\Console\Input\InputInterface** |  |
| `$output` | **?\Symfony\Component\Console\Output\OutputInterface** |  |




**Throws:**

- [`Exception`](../../../Exception.md)



***

### schedule



```php
protected schedule(\Codefy\Framework\Scheduler\Schedule $schedule): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$schedule` | **\Codefy\Framework\Scheduler\Schedule** |  |





***

### commands



```php
protected commands(): void
```












***

### registerCommand

Registers a command.

```php
public registerCommand(callable|\Symfony\Component\Console\Command\Command $command): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$command` | **callable&#124;\Symfony\Component\Console\Command\Command** |  |





***

### addCommands

Add an array of commands to the console.

```php
public addCommands(array $commands): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$commands` | **array** |  |





***

### all

Gets all the commands registered.

```php
public all(): array
```












***

### output

Get the output for the last run command.

```php
public output(): string
```












***

### bootstrap

Bootstrap the console kernel.

```php
public bootstrap(): void
```












***

### getCodex

Retrieve the Codex instance.

```php
protected getCodex(): \Codefy\Framework\Console\ConsoleApplication
```












***

### load



```php
protected load(array $commands = []): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$commands` | **array** |  |





***

### call

Run a Codex console command by name.

```php
public call(string $command, array $parameters = [], bool|\Symfony\Component\Console\Output\OutputInterface|null $outputBuffer = null): int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$command` | **string** |  |
| `$parameters` | **array** |  |
| `$outputBuffer` | **bool&#124;\Symfony\Component\Console\Output\OutputInterface&#124;null** |  |




**Throws:**

- [`CommandNotFoundException`](../../../Symfony/Component/Console/Exception/CommandNotFoundException.md)

- [`Exception`](../../../Exception.md)



***

### bootstrappers

Get the bootstrappers.

```php
protected bootstrappers(): string[]
```












***


***
> Automatically generated on 2025-10-13
