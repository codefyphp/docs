***

# Indenter





* Full name: `\Qubus\Support\Indenter`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`ELEMENT_TYPE_BLOCK`|public| |0|
|`ELEMENT_TYPE_INLINE`|public| |1|
|`MATCH_INDENT_NO`|public| |0|
|`MATCH_INDENT_DECREASE`|public| |1|
|`MATCH_INDENT_INCREASE`|public| |2|
|`MATCH_DISCARD`|public| |3|

## Properties


### log



```php
public array $log
```






***

### options



```php
private array $options
```






***

### inlineElements



```php
private array $inlineElements
```






***

### ignoreElements



```php
private array $ignoreElements
```






***

### temporaryReplacementsScript



```php
private array $temporaryReplacementsScript
```






***

### temporaryReplacementsIgnore



```php
private array $temporaryReplacementsIgnore
```






***

### temporaryReplacementsInline



```php
private array $temporaryReplacementsInline
```






***

## Methods


### __construct



```php
public __construct(array $options = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$options` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### setElementType



```php
public setElementType(string $elementName, \Qubus\Support\Indenter::ELEMENT_TYPE_BLOCK|\Qubus\Support\Indenter::ELEMENT_TYPE_INLINE $type): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$elementName` | **string** | Element name, e.g. &quot;b&quot;. |
| `$type` | **\Qubus\Support\Indenter::ELEMENT_TYPE_BLOCK&#124;\Qubus\Support\Indenter::ELEMENT_TYPE_INLINE** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### indent



```php
public indent(string|null $input = null): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$input` | **string&#124;null** | HTML input. |


**Return Value:**

Indented HTML.




***


***
> Automatically generated on 2025-10-13
