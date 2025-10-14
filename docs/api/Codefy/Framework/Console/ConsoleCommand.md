***

# ConsoleCommand





* Full name: `\Codefy\Framework\Console\ConsoleCommand`
* Parent class: [`Command`](../../../Symfony/Component/Console/Command/Command.md)
* This class is an **Abstract class**



## Properties


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

### input



```php
protected \Symfony\Component\Console\Input\InputInterface $input
```






***

### output



```php
protected \Symfony\Component\Console\Output\OutputInterface $output
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

- [`\ReflectionException|\Qubus\Exception\Data\TypeException`](../../../ReflectionException|/Qubus/Exception/Data/TypeException.md)



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

### setArguments

$arg[0] = argument name, $arg[1] = argument type and $arg[2] = argument description.

```php
private setArguments(): \Codefy\Framework\Console\ConsoleCommand|bool
```











**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



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

### setOptions



```php
private setOptions(): bool|\Codefy\Framework\Console\ConsoleCommand
```











**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***


***
> Automatically generated on 2025-10-13
