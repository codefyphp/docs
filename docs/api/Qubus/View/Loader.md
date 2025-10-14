***

# Loader





* Full name: `\Qubus\View\Loader`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Qubus\View\Renderer`](./Renderer.md)
* This class is a **Final class**


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`VERSION`|public| |&#039;3.0.0&#039;|
|`CLASS_PREFIX`|public| |&#039;__ScaffoldTemplate_&#039;|
|`RECOMPILE_NEVER`|public| |-1|
|`RECOMPILE_NORMAL`|public| |0|
|`RECOMPILE_ALWAYS`|public| |1|

## Properties


### exceptionHandler



```php
private bool $exceptionHandler
```






***

### target



```php
private \Qubus\View\Adapter\Adapter $target
```






***

### options



```php
private array $options
```






***

### paths



```php
private array $paths
```






***

### cache



```php
private array $cache
```






***

### extension



```php
private string $extension
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





***

### handleSyntaxError



```php
protected handleSyntaxError(mixed $exception): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$exception` | **mixed** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### getTemplateExtension

Get the expected extension of the template file.

```php
private getTemplateExtension(): string
```












***

### removeExtension

Remove Extension from file.

```php
private removeExtension(string $fileName): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$fileName` | **string** |  |





***

### getClassName



```php
private getClassName(string $path): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **string** |  |





***

### normalizePath



```php
public normalizePath(string $path): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **string** |  |





***

### resolvePath



```php
public resolvePath(string $template, string $from = &#039;&#039;): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$template` | **string** |  |
| `$from` | **string** |  |





***

### getAdapter



```php
protected getAdapter(): \Qubus\View\Adapter\Adapter
```












***

### compile



```php
public compile(string $template, mixed $mode = null): \Qubus\View\Loader
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$template` | **string** |  |
| `$mode` | **mixed** |  |





***

### load



```php
public load(string|\Qubus\View\Template $template, string $from = &#039;&#039;): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$template` | **string&#124;\Qubus\View\Template** |  |
| `$from` | **string** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### compileOrFail



```php
private compileOrFail(\Qubus\View\Adapter\Adapter $adapter, string $path, string $class, string $classFile): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$adapter` | **\Qubus\View\Adapter\Adapter** |  |
| `$path` | **string** |  |
| `$class` | **string** |  |
| `$classFile` | **string** |  |





***

### loadFromString



```php
public loadFromString(mixed $template): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$template` | **mixed** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### render



```php
public render(\Qubus\View\Template|string $template, array $data = []): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$template` | **\Qubus\View\Template&#124;string** |  |
| `$data` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### renderString



```php
public renderString(mixed $source, array $data = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$source` | **mixed** |  |
| `$data` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### getVersion



```php
public getVersion(): string
```












***

### setExceptionHandler



```php
public setExceptionHandler(bool $bool = true): \Qubus\View\Loader
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$bool` | **bool** |  |





***


***
> Automatically generated on 2025-10-13
