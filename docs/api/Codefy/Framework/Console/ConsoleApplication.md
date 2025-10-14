***

# ConsoleApplication





* Full name: `\Codefy\Framework\Console\ConsoleApplication`
* Parent class: [`Application`](../../../Symfony/Component/Console/Application.md)



## Properties


### lastOutput



```php
private \Symfony\Component\Console\Output\OutputInterface|string|null $lastOutput
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

### run



```php
public run(?\Symfony\Component\Console\Input\InputInterface $input = null, ?\Symfony\Component\Console\Output\OutputInterface $output = null): int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$input` | **?\Symfony\Component\Console\Input\InputInterface** |  |
| `$output` | **?\Symfony\Component\Console\Output\OutputInterface** |  |





***

### call



```php
public call(mixed $command, array $parameters = [], bool|\Symfony\Component\Console\Output\OutputInterface|null $outputBuffer = null): int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$command` | **mixed** |  |
| `$parameters` | **array** |  |
| `$outputBuffer` | **bool&#124;\Symfony\Component\Console\Output\OutputInterface&#124;null** |  |




**Throws:**

- [`Exception`](../../../Exception.md)



***

### parseCommand

Parse the incoming Codex command and its input.

```php
protected parseCommand(string $command, array $parameters): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$command` | **string** |  |
| `$parameters` | **array** |  |





***

### output

Get the output for the last run command.

```php
public output(): string
```












***


***
> Automatically generated on 2025-10-13
