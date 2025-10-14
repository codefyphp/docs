***

# NativeLoader





* Full name: `\Qubus\View\Native\NativeLoader`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Qubus\View\Native\TemplateEngine`](./TemplateEngine.md)
* This class is a **Final class**



## Properties


### namespaces



```php
private array $namespaces
```






***

### functions



```php
private array $functions
```






***

### extension



```php
private string $extension
```






***

## Methods


### __construct

Constructor for the engine.

```php
public __construct(array $namespaces = [], array $functions = [], string $extension = &#039;phtml&#039;): mixed
```

The key of the entries into the namespaces array should be the namespace
and the value should be the root directory path for templates in that
namespace.

The key of the entries to the functions array should be the method name
to hook in the template context and the value should be a callable to
invoke when this method is called.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$namespaces` | **array** | The template namespaces to register. |
| `$functions` | **array** | The functions to register. |
| `$extension` | **string** | The file extension of the templates. |





***

### render



```php
public render(string $template, array $data = []): ?string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$template` | **string** |  |
| `$data` | **array** |  |




**Throws:**

- [`ViewException`](./Exception/ViewException.md)

- [`InvalidTemplateNameException`](./Exception/InvalidTemplateNameException.md)



***

### exists

Check to see if a template exists.

```php
public exists(string $name): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | The service name. |


**Return Value:**

True if the container has the service, false otherwise.




***

### getTemplatePath

Convert a template name to a file path.

```php
public getTemplatePath(string $name): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | The template name. |


**Return Value:**

The file path of the template.




***

### callFunction

Call a function that has been registered with the templating engine.

```php
public callFunction(string|callable $name, array $arguments = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string&#124;callable** | The function name. |
| `$arguments` | **array** | The arguments to supply to the function. |


**Return Value:**

The function result.



**Throws:**

- [`FunctionDoesNotExistException`](./Exception/FunctionDoesNotExistException.md)



***

### batch

Apply multiple functions to variable.

```php
public batch(string $var, string $functions): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$var` | **string** |  |
| `$functions` | **string** |  |





***


***
> Automatically generated on 2025-10-13
