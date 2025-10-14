***

# FenomView





* Full name: `\Codefy\Framework\View\FenomView`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Qubus\View\Renderer`](../../../Qubus/View/Renderer.md)
* This class is a **Final class**



## Properties


### fenom



```php
private \Fenom $fenom
```






***

### configContainer



```php
protected \Qubus\Config\ConfigContainer $configContainer
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Config\ConfigContainer $configContainer): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$configContainer` | **\Qubus\Config\ConfigContainer** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

- [`Exception`](../../../Qubus/Exception/Exception.md)



***

### render



```php
public render(array|string $template, array $data = []): string|array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$template` | **array&#124;string** |  |
| `$data` | **array** |  |




**Throws:**

- [`CompileException`](../../../Fenom/Error/CompileException.md)



***


***
> Automatically generated on 2025-10-13
