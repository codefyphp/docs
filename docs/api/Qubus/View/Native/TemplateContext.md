***

# TemplateContext





* Full name: `\Qubus\View\Native\TemplateContext`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### parentTemplate



```php
private ?string $parentTemplate
```






***

### parentParams



```php
private array $parentParams
```






***

### engine



```php
private \Qubus\View\Native\TemplateEngine $engine
```






***

### name



```php
private string $name
```






***

### params



```php
private array $params
```






***

### blocks



```php
private array $blocks
```






***

## Methods


### __construct

Constructor for the template context.

```php
public __construct(\Qubus\View\Native\TemplateEngine $engine, string $name, array $params = [], array $blocks = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$engine` | **\Qubus\View\Native\TemplateEngine** | The templating engine. |
| `$name` | **string** | The template name. |
| `$params` | **array** | The template parameters. |
| `$blocks` | **array** | Child template blocks |





***

### __invoke

Invoke the template and return the generated content.

```php
public __invoke(): \Qubus\View\Native\TemplateResult
```









**Return Value:**

The result of the template.



**Throws:**
<p>If an error is encountered rendering the template.</p>

- [`ViewException`](./Exception/ViewException.md)

- [`InvalidTemplateNameException`](./Exception/InvalidTemplateNameException.md)



***

### getOutput

Get output from callable

```php
private getOutput(callable $callback): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **callable** | The callback to get the output from. |





***

### parent

Define a parent template.

```php
public parent(string $template, array $params = []): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$template` | **string** | The name of the parent template. |
| `$params` | **array** | Parameters to add to the parent template context |




**Throws:**
<p>If a parent template has already been defined.</p>

- [`ViewException`](./Exception/ViewException.md)



***

### insert

Insert a template.

```php
public insert(string $template, array $params = []): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$template` | **string** | The name of the template. |
| `$params` | **array** | Parameters to add to the template context |





***

### block

Render a block.

```php
public block(string $name, ?callable $callback = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | The name of the block. |
| `$callback` | **?callable** |  |




**Throws:**

- [`ViewException`](./Exception/ViewException.md)



***

### esc

Escaping for HTML output.

```php
public esc(string $string, string|null $functions = null): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** | Html element to escape. |
| `$functions` | **string&#124;null** | Functions to run the string through. |


**Return Value:**

Escaped HTML output.




***

### escJs

Escaping for inline javascript.

```php
public escJs(string $string): string
```

Example usage:

$esc_js = json_encode("Joshua's \"code\"");
$attribute = esc_js("alert($esc_js);");
echo '<input type="button" value="push" onclick="'.$attribute.'" />';






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** | The string to be escaped. |


**Return Value:**

Escaped inline javascript.




***

### escUrl

Escaping for url.

```php
public escUrl(string $url, array $scheme = [], bool $encode = false): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$url` | **string** | The url to be escaped. |
| `$scheme` | **array** | Optional. An array of acceptable schemes. |
| `$encode` | **bool** | Whether url params should be encoded. |


**Return Value:**

The escaped $url.




***

### purify

Makes content safe to print on screen.

```php
public purify(string $string): string
```

This function should only be used on output, with the exception of uploading
images, never use this function on input. All inputted data should be
accepted and then purified on output for optimal results. For output of images,
make sure to escape with esc_url().






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** | Text to purify. |





***

### truncate

Truncates a string to the given length. It will optionally preserve
HTML tags if $isHtml is set to true.

```php
public truncate(string $string, int $limit, string $continuation = &#039;...&#039;, bool $isHtml = false): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** | The string to truncate. |
| `$limit` | **int** | The number of characters to truncate. |
| `$continuation` | **string** | The string to use to denote it was truncated. |
| `$isHtml` | **bool** | Whether the string has HTML. |


**Return Value:**

The truncated string.




***

### concat

Concatenation with separator.

```php
public concat(string $string1, string $string2, string $separator = &#039;,&#039;, string $strings): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string1` | **string** | Left string. |
| `$string2` | **string** | Right string. |
| `$separator` | **string** | Delimiter to use between strings. Default: comma. |
| `$strings` | **string** | List of strings. |


**Return Value:**

Concatenated string.




***

### __call

Delegate a method call to the templating engine to see if a function has
been defined.

```php
public __call(string $name, array $arguments): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | The method name being called. |
| `$arguments` | **array** | The arguments provided to the method. |


**Return Value:**

The function result.




***


***
> Automatically generated on 2025-10-13
