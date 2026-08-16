# GeneratorCommand

***

* Full name: `\Codefy\Framework\Console\Commands\Domain\GeneratorCommand`
* Parent class: [`\Codefy\Framework\Console\ConsoleCommand`](../../ConsoleCommand.md)
* This class is an **Abstract class**

## Properties

### type

The type of class being generated.

```php
protected string $type
```

***

### codefy

```php
protected \Codefy\Framework\Application $codefy
```

***

### filesystem

```php
protected \Qubus\FileSystem\FileSystem $filesystem
```

***

## Methods

### __construct

```php
public __construct(\Codefy\Framework\Application $codefy, \Qubus\FileSystem\FileSystem $filesystem): mixed
```

**Parameters:**

| Parameter     | Type                              | Description |
|---------------|-----------------------------------|-------------|
| `$codefy`     | **\Codefy\Framework\Application** |             |
| `$filesystem` | **\Qubus\FileSystem\FileSystem**  |             |

***

### getStub

Get the stub file for the generator.

```php
protected getStub(): string
```

* This method is **abstract**.
***

### handle

```php
public handle(): int
```

**Throws:**

- [`Exception`](../../../../../Qubus/Exception/Exception.md)
- [`FilesystemException`](../../../../../League/Flysystem/FilesystemException.md)
- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)

***

### qualifyClass

Parse the class name and format according to the root namespace.

```php
protected qualifyClass(string $name): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

**Throws:**

- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)

***

### getDefaultNamespace

Get the default namespace for the class.

```php
protected getDefaultNamespace(string $rootNamespace): string
```

**Parameters:**

| Parameter        | Type       | Description |
|------------------|------------|-------------|
| `$rootNamespace` | **string** |             |

***

### alreadyExists

Determine if the class already exists.

```php
protected alreadyExists(string $rawName): bool
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$rawName` | **string** |             |

**Throws:**

- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)
- [`NotFoundException`](../../../../../Qubus/Exception/Http/Client/NotFoundException.md)

***

### getPath

Get the destination class path.

```php
protected getPath(string $name): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

**Throws:**

- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)

***

### makeDirectory

Build the directory for the class if necessary.

```php
protected makeDirectory(string $path): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$path`   | **string** |             |

**Throws:**

- [`FilesystemException`](../../../../../League/Flysystem/FilesystemException.md)
- [`Exception`](../../../../../Qubus/Exception/Exception.md)

***

### buildClass

Build the class with the given name.

```php
protected buildClass(string $name): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

**Throws:**

- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)

***

### replaceNamespace

Replace the namespace for the given stub.

```php
protected replaceNamespace(string& $stub, string $name): $this
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$stub`   | **string** |             |
| `$name`   | **string** |             |

**Throws:**

- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)

***

### getNamespace

Get the full namespace for a given class, without the class name.

```php
protected getNamespace(string $name): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### replaceClass

Replace the class name for the given stub.

```php
protected replaceClass(string $stub, string $name): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$stub`   | **string** |             |
| `$name`   | **string** |             |

***

### sortImports

Alphabetically sorts the imports for the given stub.

```php
protected sortImports(string $stub): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$stub`   | **string** |             |

***

### getNameInput

Get the desired class name from the input.

```php
protected getNameInput(): string
```

***

### rootNamespace

Get the root namespace for the class.

```php
protected rootNamespace(): string
```

**Throws:**

- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)

***

### getArguments

Get the console command arguments.

```php
protected getArguments(): array
```

***

### promptForMissingArgumentsUsing

Prompt for missing input arguments using the returned questions.

```php
protected promptForMissingArgumentsUsing(): array
```

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

- [`ReflectionException`](../../../../../ReflectionException.md)
- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)

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

- [`ExceptionInterface`](../../../../../Symfony/Component/Console/Exception/ExceptionInterface.md)

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

- [`ExceptionInterface`](../../../../../Symfony/Component/Console/Exception/ExceptionInterface.md)

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
