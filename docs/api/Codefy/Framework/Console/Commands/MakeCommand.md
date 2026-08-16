# MakeCommand

***

* Full name: `\Codefy\Framework\Console\Commands\MakeCommand`
* Parent class: [`\Codefy\Framework\Console\ConsoleCommand`](../ConsoleCommand.md)
* **Warning:** this class is **deprecated**. This means that this class will likely be removed in a future version.

**See Also:**

* \Codefy\Framework\Console\Commands\Domain\MakeDomainCommand
* \Codefy\Framework\Console\Commands\Domain\MakeCommand
* https://codefyphp.com/docs/getting-started/codex/

## Constants

| Constant         | Visibility | Type | Value                                                                                                                                                                                                                                                                                                                                                          |
|------------------|------------|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `FILE_EXTENSION` | protected  |      | '.php'                                                                                                                                                                                                                                                                                                                                                         |
| `STUBS`          | private    |      | ['controller' => 'App\Infrastructure\Http\Controllers', 'repository' => 'App\Infrastructure\Persistence\Repository', 'provider' => 'App\Infrastructure\Providers', 'middleware' => 'App\Infrastructure\Http\Middleware', 'error' => 'App\Infrastructure\Errors', 'command' => 'App\Application\Console\Commands', 'route' => 'App\Infrastructure\Http\Routes'] |

## Properties

### errors

```php
private array $errors
```

***

### comments

```php
private array $comments
```

***

### info

```php
private array $info
```

***

### name

```php
protected string $name
```

***

### description

```php
protected string $description
```

***

### help

```php
protected string $help
```

***

### args

Refers to name, type, description argument.

```php
protected array $args
```

***

### options

Refers to name, shortcut, type, description and default.

```php
protected array $options
```

***

## Methods

### handle

```php
public handle(): int
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

### resolveResource

```php
private resolveResource(string $resource, mixed $options): void
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$resource` | **string** |             |
| `$options`  | **mixed**  |             |

**Throws:**

- [`TypeException`](../../../../Qubus/Exception/Data/TypeException.md)
- [`MakeCommandFileAlreadyExistsException`](../Exceptions/MakeCommandFileAlreadyExistsException.md)
- [`ReflectionException`](../../../../ReflectionException.md)

***

### resolveClassNameSuffix

```php
private resolveClassNameSuffix(string $classNameSuffix, string $classNamePrefix, mixed|null $options = null): void
```

**Parameters:**

| Parameter          | Type            | Description |
|--------------------|-----------------|-------------|
| `$classNameSuffix` | **string**      |             |
| `$classNamePrefix` | **string**      |             |
| `$options`         | **mixed\|null** |             |

**Throws:**

- [`MakeCommandFileAlreadyExistsException`](../Exceptions/MakeCommandFileAlreadyExistsException.md)
- [`ReflectionException`](../../../../ReflectionException.md)
- [`TypeException`](../../../../Qubus/Exception/Data/TypeException.md)
- [`Exception`](../../../../Exception.md)

***

### createClassFromStub

Create the class file based on the stub file. Once the file is resolved and have a valid directory path
and the stub content is properly filtered and change to reflect. Then and only then we will
generate the actual usable class file.

```php
public createClassFromStub(string $qualifiedClass, string|null $contentStream = null, string|null $classNameSuffix = null, string|null $flag = null, string|null $qualifiedNamespaces = null): void
```

Note. realpath will return false if the file or directory does not exist.

**Parameters:**

| Parameter              | Type             | Description                                      |
|------------------------|------------------|--------------------------------------------------|
| `$qualifiedClass`      | **string**       |                                                  |
| `$contentStream`       | **string\|null** |                                                  |
| `$classNameSuffix`     | **string\|null** |                                                  |
| `$flag`                | **string\|null** |                                                  |
| `$qualifiedNamespaces` | **string\|null** | - will return the namespace for the stub command |

**Throws:**

- [`MakeCommandFileAlreadyExistsException`](../Exceptions/MakeCommandFileAlreadyExistsException.md)
- [`Exception`](../../../../Exception.md)
- [`ReflectionException`](../../../../ReflectionException.md)

***

### addOptionalDirFlag

console command option flag. Use --dir={directory_name} to add a directory to the end
of the filepath to create a subdirectory within a main directory

```php
private addOptionalDirFlag(string $flag): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$flag`   | **string** |             |

***

### getStubFiles

Uses the php glob to retrieve all stub files form the relevant directory. Which will return
an array of files within the specified directory with the [.stub] extension.

```php
private getStubFiles(string $classNameSuffix): string|false
```

We then iterate over that array and uses php str_contain function to match a file from
the array with the classNameSuffix. When we have a match then return the matching file string.

**Parameters:**

| Parameter          | Type       | Description |
|--------------------|------------|-------------|
| `$classNameSuffix` | **string** |             |

***

### resolveStubContentPlaceholders

```php
private resolveStubContentPlaceholders(string $file, string $classNameSuffix, string $classNamePrefix): array|bool
```

**Parameters:**

| Parameter          | Type       | Description |
|--------------------|------------|-------------|
| `$file`            | **string** |             |
| `$classNameSuffix` | **string** |             |
| `$classNamePrefix` | **string** |             |

***

### resolveModelDependency

Resolve the model dependency by specifying which Stubs class will require a model.

```php
private resolveModelDependency(string $classNamePrefix, string $classNameSuffix): array|bool
```

**Parameters:**

| Parameter          | Type       | Description |
|--------------------|------------|-------------|
| `$classNamePrefix` | **string** |             |
| `$classNameSuffix` | **string** |             |

***
