***

# Module





* Full name: `\Qubus\View\Module`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### path



```php
private string $path
```






***

### class



```php
private string $class
```






***

### extends



```php
private $extends
```






***

### imports



```php
private array $imports
```






***

### blocks



```php
private array $blocks
```






***

### macros



```php
private array $macros
```






***

### body



```php
private \Qubus\View\BaseNode $body
```






***

## Methods


### __construct



```php
public __construct(string $path, string $class, mixed $extends, array $imports, array $blocks, array $macros, \Qubus\View\BaseNode $body): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **string** |  |
| `$class` | **string** |  |
| `$extends` | **mixed** |  |
| `$imports` | **array** |  |
| `$blocks` | **array** |  |
| `$macros` | **array** |  |
| `$body` | **\Qubus\View\BaseNode** |  |





***

### compile



```php
public compile(mixed $compiler, mixed $indent): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$compiler` | **mixed** |  |
| `$indent` | **mixed** |  |





***


***
> Automatically generated on 2025-10-13
