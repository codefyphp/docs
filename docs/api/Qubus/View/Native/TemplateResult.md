***

# TemplateResult





* Full name: `\Qubus\View\Native\TemplateResult`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### content



```php
private string $content
```






***

### blocks



```php
private array $blocks
```






***

## Methods


### __construct

Constructor for the template result.

```php
public __construct(string $content, array $blocks = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$content` | **string** | The template content. |
| `$blocks` | **array** | The template blocks. |





***

### getContent

Get the content of the result.

```php
public getContent(): string
```









**Return Value:**

The content of the template result.




***

### getBlocks

Get the blocks of the result.

```php
public getBlocks(): array
```









**Return Value:**

The blocks of the template result.




***


***
> Automatically generated on 2025-10-13
