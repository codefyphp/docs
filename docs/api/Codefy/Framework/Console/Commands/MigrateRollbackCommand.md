***

# MigrateRollbackCommand





* Full name: `\Codefy\Framework\Console\Commands\MigrateRollbackCommand`
* Parent class: [`\Codefy\Framework\Console\Commands\PhpMigCommand`](./PhpMigCommand.md)



## Properties


### name



```php
protected string $name
```






***

## Methods


### configure

Configure commands.

```php
protected configure(): void
```












***

### handle



```php
public handle(): int
```











**Throws:**

- [`Exception`](../../../../Qubus/Exception/Exception.md)



***


## Inherited methods


### __construct



```php
public __construct(\Codefy\Framework\Application $codefy): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$codefy` | **\Codefy\Framework\Application** |  |





***

### configure

Configure commands.

```php
protected configure(): void
```












***

### execute



```php
protected execute(\Symfony\Component\Console\Input\InputInterface $input, \Symfony\Component\Console\Output\OutputInterface $output): int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$input` | **\Symfony\Component\Console\Input\InputInterface** |  |
| `$output` | **\Symfony\Component\Console\Output\OutputInterface** |  |




**Throws:**

- [`\ReflectionException|\Qubus\Exception\Data\TypeException`](../../../../ReflectionException|/Qubus/Exception/Data/TypeException.md)



***

### getArgument

Returns the argument value for the given argument name.

```php
protected getArgument(string|null $key = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string&#124;null** |  |





***

### getOptions

Returns the option value for the given option name.

```php
protected getOptions(string|null $key = null): bool|string|string[]
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string&#124;null** |  |





***

### terminalRaw

Outputs the string to the console without any tag.

```php
protected terminalRaw(string $string): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |





***

### terminalInfo

Output to the terminal wrap in info tags.

```php
protected terminalInfo(string $string): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |





***

### terminalComment

Output to the terminal wrap in comment tags.

```php
protected terminalComment(string $string): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |





***

### terminalQuestion

Output to the terminal wrap in question tags.

```php
protected terminalQuestion(string $string): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |





***

### terminalError

Output to the terminal wrap in error tags.

```php
protected terminalError(string $string): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |





***

### terminalNewLine

Output to the terminal with a blank line.

```php
protected terminalNewLine(int $count = 1): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$count` | **int** |  |





***

### confirm



```php
protected confirm(string $question): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$question` | **string** |  |





***

### ask



```php
protected ask(string $question, bool|float|int|string|null $default = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$question` | **string** |  |
| `$default` | **bool&#124;float&#124;int&#124;string&#124;null** |  |





***

### choice



```php
protected choice(string $question, array $choices, bool|float|int|string|null $default = null, string|null $message = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$question` | **string** |  |
| `$choices` | **array** |  |
| `$default` | **bool&#124;float&#124;int&#124;string&#124;null** |  |
| `$message` | **string&#124;null** |  |





***

### multiChoice



```php
protected multiChoice(string $question, array $choices, bool|float|int|string|null $default = null, string|null $message = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$question` | **string** |  |
| `$choices` | **array** |  |
| `$default` | **bool&#124;float&#124;int&#124;string&#124;null** |  |
| `$message` | **string&#124;null** |  |





***

### bootstrap

Bootstrap migration.

```php
protected bootstrap(\Symfony\Component\Console\Input\InputInterface $input, \Symfony\Component\Console\Output\OutputInterface $output): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$input` | **\Symfony\Component\Console\Input\InputInterface** |  |
| `$output` | **\Symfony\Component\Console\Output\OutputInterface** |  |




**Throws:**

- [`Exception`](../../../../Qubus/Exception/Exception.md)

- [`TypeException`](../../../../Qubus/Exception/Data/TypeException.md)



***

### findBootstrapFile



```php
protected findBootstrapFile(mixed $filename): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$filename` | **mixed** |  |





***

### bootstrapObjectMap



```php
protected bootstrapObjectMap(): \ArrayAccess
```












***

### bootstrapAdapter



```php
protected bootstrapAdapter(\Symfony\Component\Console\Input\InputInterface $input): \Qubus\Expressive\Migration\Adapter\MigrationAdapter
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$input` | **\Symfony\Component\Console\Input\InputInterface** |  |




**Throws:**

- [`RuntimeException`](../../../../RuntimeException.md)



***

### bootstrapMigrations



```php
protected bootstrapMigrations(\Symfony\Component\Console\Input\InputInterface $input, \Symfony\Component\Console\Output\OutputInterface $output): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$input` | **\Symfony\Component\Console\Input\InputInterface** |  |
| `$output` | **\Symfony\Component\Console\Output\OutputInterface** |  |




**Throws:**

- [`TypeException`](../../../../Qubus/Exception/Data/TypeException.md)



***

### bootstrapMigrator



```php
protected bootstrapMigrator(\Symfony\Component\Console\Output\OutputInterface $output): \Qubus\Expressive\Migration\Migrator
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$output` | **\Symfony\Component\Console\Output\OutputInterface** |  |





***

### setBootstrap

Set bootstrap.

```php
public setBootstrap(string $bootstrap): \Codefy\Framework\Console\Commands\PhpMigCommand
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$bootstrap` | **string** |  |





***

### getBootstrap

Get bootstrap

```php
public getBootstrap(): string|null
```












***

### setMigrations

Set migrations

```php
public setMigrations(array $migrations): \Codefy\Framework\Console\Commands\PhpMigCommand
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$migrations` | **array** |  |





***

### getMigrations

Get migrations.

```php
public getMigrations(): array
```












***

### setObjectMap

Set objectmap.

```php
public setObjectMap(\ArrayAccess $objectmap): \Codefy\Framework\Console\Commands\PhpMigCommand
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$objectmap` | **\ArrayAccess** |  |





***

### getObjectMap

Get objectmap.

```php
public getObjectMap(): \ArrayAccess|null
```












***

### setAdapter

Set adapter.

```php
public setAdapter(\Qubus\Expressive\Migration\Adapter\MigrationAdapter $adapter): \Codefy\Framework\Console\Commands\PhpMigCommand
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$adapter` | **\Qubus\Expressive\Migration\Adapter\MigrationAdapter** |  |





***

### getAdapter

Get Adapter

```php
public getAdapter(): \Qubus\Expressive\Migration\Adapter\MigrationAdapter|null
```












***

### migrationToClassName

Transform create_table_user to CreateTableUser

```php
protected migrationToClassName(mixed $migrationName): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$migrationName` | **mixed** |  |




**Throws:**

- [`TypeException`](../../../../Qubus/Exception/Data/TypeException.md)



***


***
> Automatically generated on 2025-10-13
