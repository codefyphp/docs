# PhpMigCommand

***

* Full name: `\Codefy\Framework\Console\Commands\PhpMigCommand`
* Parent class: [`\Codefy\Framework\Console\ConsoleCommand`](../ConsoleCommand.md)
* This class is an **Abstract class**

## Properties

### objectmap

```php
protected ?\ArrayAccess $objectmap
```

***

### adapter

```php
protected ?\Qubus\Expressive\Migration\Adapter\MigrationAdapter $adapter
```

***

### bootstrap

```php
protected ?string $bootstrap
```

***

### migrations

```php
protected array $migrations
```

***

## Methods

### configure

Configure commands.

```php
protected configure(): void
```

***

### bootstrap

Bootstrap migration.

```php
protected bootstrap(\Symfony\Component\Console\Input\InputInterface $input, \Symfony\Component\Console\Output\OutputInterface $output): void
```

**Parameters:**

| Parameter | Type                                                  | Description |
|-----------|-------------------------------------------------------|-------------|
| `$input`  | **\Symfony\Component\Console\Input\InputInterface**   |             |
| `$output` | **\Symfony\Component\Console\Output\OutputInterface** |             |

**Throws:**

- [`Exception`](../../../../Qubus/Exception/Exception.md)
- [`TypeException`](../../../../Qubus/Exception/Data/TypeException.md)

***

### findBootstrapFile

```php
protected findBootstrapFile(string|null $filename = null): string
```

**Parameters:**

| Parameter   | Type             | Description |
|-------------|------------------|-------------|
| `$filename` | **string\|null** |             |

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

| Parameter | Type                                                | Description |
|-----------|-----------------------------------------------------|-------------|
| `$input`  | **\Symfony\Component\Console\Input\InputInterface** |             |

**Throws:**

- [`RuntimeException`](../../../../RuntimeException.md)

***

### bootstrapMigrations

```php
protected bootstrapMigrations(\Symfony\Component\Console\Input\InputInterface $input, \Symfony\Component\Console\Output\OutputInterface $output): array
```

**Parameters:**

| Parameter | Type                                                  | Description |
|-----------|-------------------------------------------------------|-------------|
| `$input`  | **\Symfony\Component\Console\Input\InputInterface**   |             |
| `$output` | **\Symfony\Component\Console\Output\OutputInterface** |             |

**Throws:**

- [`TypeException`](../../../../Qubus/Exception/Data/TypeException.md)

***

### bootstrapMigrator

```php
protected bootstrapMigrator(\Symfony\Component\Console\Output\OutputInterface $output): \Qubus\Expressive\Migration\Migrator
```

**Parameters:**

| Parameter | Type                                                  | Description |
|-----------|-------------------------------------------------------|-------------|
| `$output` | **\Symfony\Component\Console\Output\OutputInterface** |             |

***

### setBootstrap

Set bootstrap.

```php
public setBootstrap(string $bootstrap): static
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$bootstrap` | **string** |             |

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
public setMigrations(array $migrations): static
```

**Parameters:**

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `$migrations` | **array** |             |

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
public setObjectMap(\ArrayAccess $objectmap): static
```

**Parameters:**

| Parameter    | Type             | Description |
|--------------|------------------|-------------|
| `$objectmap` | **\ArrayAccess** |             |

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
public setAdapter(\Qubus\Expressive\Migration\Adapter\MigrationAdapter $adapter): static
```

**Parameters:**

| Parameter  | Type                                                     | Description |
|------------|----------------------------------------------------------|-------------|
| `$adapter` | **\Qubus\Expressive\Migration\Adapter\MigrationAdapter** |             |

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

| Parameter        | Type      | Description |
|------------------|-----------|-------------|
| `$migrationName` | **mixed** |             |

**Throws:**

- [`TypeException`](../../../../Qubus/Exception/Data/TypeException.md)

***

### isValidClassName

```php
private isValidClassName(mixed $className): bool
```

**Parameters:**

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `$className` | **mixed** |             |

**See Also:**

* http://php.net/manual/en/language.oop5.basic.php#language.oop5.basic.class

***

## Inherited methods

### __construct

```php
public __construct(\Codefy\Framework\Application $codefy): mixed
```

**Parameters:**

| Parameter | Type                              | Description |
|-----------|-----------------------------------|-------------|
| `$codefy` | **\Codefy\Framework\Application** |             |

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

| Parameter | Type                                                  | Description |
|-----------|-------------------------------------------------------|-------------|
| `$input`  | **\Symfony\Component\Console\Input\InputInterface**   |             |
| `$output` | **\Symfony\Component\Console\Output\OutputInterface** |             |

**Throws:**

- [`ReflectionException`](../../../../ReflectionException.md)
- [`TypeException`](../../../../Qubus/Exception/Data/TypeException.md)

***

### getArgument

Returns the argument value for the given argument name.

```php
protected getArgument(string|null $key = null): mixed
```

**Parameters:**

| Parameter | Type             | Description |
|-----------|------------------|-------------|
| `$key`    | **string\|null** |             |

***

### getOptions

Returns the option value for the given option name.

```php
protected getOptions(string|null $key = null): bool|string|string[]|null
```

**Parameters:**

| Parameter | Type             | Description |
|-----------|------------------|-------------|
| `$key`    | **string\|null** |             |

***

### terminalRaw

Outputs the string to the console without any tag.

```php
protected terminalRaw(string $string): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$string` | **string** |             |

***

### terminalInfo

Output to the terminal wrap in info tags.

```php
protected terminalInfo(string $string): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$string` | **string** |             |

***

### terminalComment

Output to the terminal wrap in comment tags.

```php
protected terminalComment(string $string): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$string` | **string** |             |

***

### terminalQuestion

Output to the terminal wrap in question tags.

```php
protected terminalQuestion(string $string): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$string` | **string** |             |

***

### terminalError

Output to the terminal wrap in error tags.

```php
protected terminalError(string $string): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$string` | **string** |             |

***

### terminalNewLine

Output to the terminal with a blank line.

```php
protected terminalNewLine(int $count = 1): void
```

**Parameters:**

| Parameter | Type    | Description |
|-----------|---------|-------------|
| `$count`  | **int** |             |

***

### confirm

```php
protected confirm(string $question): mixed
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$question` | **string** |             |

***

### ask

```php
protected ask(string $question, bool|float|int|string|null $default = null): mixed
```

**Parameters:**

| Parameter   | Type                               | Description |
|-------------|------------------------------------|-------------|
| `$question` | **string**                         |             |
| `$default`  | **bool\|float\|int\|string\|null** |             |

***

### choice

```php
protected choice(string $question, (string|bool|int|float|\Stringable)[] $choices, bool|float|int|string|null $default = null, string|null $message = null): mixed
```

**Parameters:**

| Parameter   | Type                                          | Description |
|-------------|-----------------------------------------------|-------------|
| `$question` | **string**                                    |             |
| `$choices`  | **(string\|bool\|int\|float\|\Stringable)[]** |             |
| `$default`  | **bool\|float\|int\|string\|null**            |             |
| `$message`  | **string\|null**                              |             |

***

### multiChoice

```php
protected multiChoice(string $question, (string|bool|int|float|\Stringable)[] $choices, bool|float|int|string|null $default = null, string|null $message = null): mixed
```

**Parameters:**

| Parameter   | Type                                          | Description |
|-------------|-----------------------------------------------|-------------|
| `$question` | **string**                                    |             |
| `$choices`  | **(string\|bool\|int\|float\|\Stringable)[]** |             |
| `$default`  | **bool\|float\|int\|string\|null**            |             |
| `$message`  | **string\|null**                              |             |

***

### resolveCommand

Resolve the console command instance for the given command.

```php
protected resolveCommand(\Symfony\Component\Console\Command\Command|string $command): \Symfony\Component\Console\Command\Command
```

**Parameters:**

| Parameter  | Type                                                   | Description |
|------------|--------------------------------------------------------|-------------|
| `$command` | **\Symfony\Component\Console\Command\Command\|string** |             |

***

### call

Call another console command.

```php
public call(\Symfony\Component\Console\Command\Command|string $command, array $arguments = []): int
```

**Parameters:**

| Parameter    | Type                                                   | Description |
|--------------|--------------------------------------------------------|-------------|
| `$command`   | **\Symfony\Component\Console\Command\Command\|string** |             |
| `$arguments` | **array**                                              |             |

**Throws:**

- [`ExceptionInterface`](../../../../Symfony/Component/Console/Exception/ExceptionInterface.md)

***

### option

Get the value of a command option.

```php
public option(string|null $key = null): string|array|bool|null
```

**Parameters:**

| Parameter | Type             | Description |
|-----------|------------------|-------------|
| `$key`    | **string\|null** |             |

***

### options

Get all the options passed to the command.

```php
public options(): bool|array|string|null
```

***

### runCommand

Run the given console command.

```php
protected runCommand(\Symfony\Component\Console\Command\Command|string $command, array $arguments, \Symfony\Component\Console\Output\OutputInterface $output): int
```

**Parameters:**

| Parameter    | Type                                                   | Description |
|--------------|--------------------------------------------------------|-------------|
| `$command`   | **\Symfony\Component\Console\Command\Command\|string** |             |
| `$arguments` | **array**                                              |             |
| `$output`    | **\Symfony\Component\Console\Output\OutputInterface**  |             |

**Throws:**

- [`ExceptionInterface`](../../../../Symfony/Component/Console/Exception/ExceptionInterface.md)

***

### createInputFromArguments

Create an input instance from the given arguments.

```php
protected createInputFromArguments(array $arguments): \Symfony\Component\Console\Input\ArrayInput
```

**Parameters:**

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `$arguments` | **array** |             |

***

### context

Get all the context passed to the command.

```php
protected context(): array
```

***
