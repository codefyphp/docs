***

# MakeCommand





* Full name: `\Codefy\Framework\Console\Commands\MakeCommand`
* Parent class: [`\Codefy\Framework\Console\ConsoleCommand`](../ConsoleCommand.md)


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`FILE_EXTENSION`|protected| |&#039;.php&#039;|
|`STUBS`|private| |[&#039;controller&#039; =&gt; &#039;App\Infrastructure\Http\Controllers&#039;, &#039;repository&#039; =&gt; &#039;App\Infrastructure\Persistence\Repository&#039;, &#039;provider&#039; =&gt; &#039;App\Infrastructure\Providers&#039;, &#039;middleware&#039; =&gt; &#039;App\Infrastructure\Http\Middleware&#039;, &#039;error&#039; =&gt; &#039;App\Infrastructure\Errors&#039;, &#039;command&#039; =&gt; &#039;App\Application\Console\Commands&#039;, &#039;route&#039; =&gt; &#039;App\Infrastructure\Http\Routes&#039;]|

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



```php
protected array $args
```






***

### options



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

### resolveResource



```php
private resolveResource(string $resource, mixed $options): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$resource` | **string** |  |
| `$options` | **mixed** |  |




**Throws:**

- [`\Qubus\Exception\Data\TypeException|\Codefy\Framework\Console\Exceptions\MakeCommandFileAlreadyExistsException`](../../../../Qubus/Exception/Data/TypeException|/Codefy/Framework/Console/Exceptions/MakeCommandFileAlreadyExistsException.md)



***

### resolveClassNameSuffix



```php
private resolveClassNameSuffix(string $classNameSuffix, string $classNamePrefix, mixed|null $options = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$classNameSuffix` | **string** |  |
| `$classNamePrefix` | **string** |  |
| `$options` | **mixed&#124;null** |  |




**Throws:**

- [`MakeCommandFileAlreadyExistsException`](../Exceptions/MakeCommandFileAlreadyExistsException.md)

- [`TypeException`](../../../../Qubus/Exception/Data/TypeException.md)



***

### createClassFromStub

Create the class file based on the stub file. Once the file is resolved and have a valid directory path
and the stub content is properly filtered and change to reflect. Then and only then we will
generate the actual usable class file.

```php
public createClassFromStub(string $qualifiedClass, string|null $contentStream = null, string|null $classNameSuffix = null, mixed|null $options = null, string|null $qualifiedNamespaces = null): void
```

Note. realpath will return false if the file or directory does not exist.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$qualifiedClass` | **string** |  |
| `$contentStream` | **string&#124;null** |  |
| `$classNameSuffix` | **string&#124;null** |  |
| `$options` | **mixed&#124;null** |  |
| `$qualifiedNamespaces` | **string&#124;null** | - will return the namespace for the stub command |




**Throws:**

- [`MakeCommandFileAlreadyExistsException`](../Exceptions/MakeCommandFileAlreadyExistsException.md)

- [`Exception`](../../../../Qubus/Exception/Exception.md)

- [`ReflectionException`](../../../../ReflectionException.md)



***

### addOptionalDirFlag

console command option flag. Use --dir={directory_name} to add a directory to the end
of the filepath to create a subdirectory within a main directory

```php
private addOptionalDirFlag(mixed $options): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$options` | **mixed** |  |





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

| Parameter | Type | Description |
|-----------|------|-------------|
| `$classNameSuffix` | **string** |  |





***

### resolveStubContentPlaceholders



```php
private resolveStubContentPlaceholders(string $file, string $classNameSuffix, string $classNamePrefix): array|bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$file` | **string** |  |
| `$classNameSuffix` | **string** |  |
| `$classNamePrefix` | **string** |  |





***

### resolveModelDependency

Resolve the model dependency by specifying which Stubs class will require a model.

```php
private resolveModelDependency(string $classNamePrefix, string $classNameSuffix): array|bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$classNamePrefix` | **string** |  |
| `$classNameSuffix` | **string** |  |





***


***
> Automatically generated on 2025-10-13
