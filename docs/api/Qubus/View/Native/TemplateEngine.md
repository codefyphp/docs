***

# TemplateEngine





* Full name: `\Qubus\View\Native\TemplateEngine`
* Parent interfaces: [`\Qubus\View\Renderer`](../Renderer.md)


## Methods


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



**Throws:**
<p>If the template name is invalid.</p>

- [`InvalidTemplateNameException`](./Exception/InvalidTemplateNameException.md)



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



**Throws:**
<p>If the template name is invalid.</p>

- [`InvalidTemplateNameException`](./Exception/InvalidTemplateNameException.md)
<p>If the template namespace does not exist.</p>

- [`TemplateNotFoundException`](./Exception/TemplateNotFoundException.md)



***

### callFunction

Call a function that has been registered with the templating engine.

```php
public callFunction(string $name, array $arguments = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | The function name. |
| `$arguments` | **array** | The arguments to supply to the function. |


**Return Value:**

The function result.




***


***
> Automatically generated on 2025-10-13
