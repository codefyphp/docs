***

# Template





* Full name: `\Qubus\View\Template`
* This class is an **Abstract class**


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`SCAFFOLD_NAME`|public| |&#039;&#039;|

## Properties


### loader



```php
protected \Qubus\View\Loader $loader
```






***

### helpers



```php
protected array $helpers
```






***

### parent



```php
protected ?\Qubus\View\Template $parent
```






***

### blocks



```php
public array $blocks
```






***

### macros



```php
public array $macros
```






***

### imports



```php
public array $imports
```






***

### stack



```php
protected array $stack
```






***

## Methods


### __construct



```php
public __construct(\Qubus\View\Loader $loader, array $helpers = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$loader` | **\Qubus\View\Loader** |  |
| `$helpers` | **array** |  |





***

### getPath



```php
private getPath(mixed $template): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$template` | **mixed** |  |





***

### loadExtends



```php
public loadExtends(mixed $template): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$template` | **mixed** |  |





***

### loadInclude



```php
public loadInclude(mixed $template): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$template` | **mixed** |  |





***

### loadImport



```php
public loadImport(mixed $template): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$template` | **mixed** |  |





***

### displayBlock



```php
public displayBlock(mixed $name, mixed $context, mixed $blocks, mixed $macros, mixed $imports): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |
| `$context` | **mixed** |  |
| `$blocks` | **mixed** |  |
| `$macros` | **mixed** |  |
| `$imports` | **mixed** |  |





***

### displayParent



```php
public displayParent(mixed $name, mixed $context, mixed $blocks, mixed $macros, mixed $imports): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |
| `$context` | **mixed** |  |
| `$blocks` | **mixed** |  |
| `$macros` | **mixed** |  |
| `$imports` | **mixed** |  |





***

### expandMacro



```php
public expandMacro(mixed $module, mixed $name, mixed $params, mixed $context, mixed $macros, mixed $imports, mixed $block): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$module` | **mixed** |  |
| `$name` | **mixed** |  |
| `$params` | **mixed** |  |
| `$context` | **mixed** |  |
| `$macros` | **mixed** |  |
| `$imports` | **mixed** |  |
| `$block` | **mixed** |  |





***

### pushContext



```php
public pushContext(mixed& $context, mixed $name): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$context` | **mixed** |  |
| `$name` | **mixed** |  |





***

### popContext



```php
public popContext(mixed& $context, mixed $name): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$context` | **mixed** |  |
| `$name` | **mixed** |  |





***

### getLineTrace



```php
public getLineTrace(?\Qubus\Exception\Exception $e = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$e` | **?\Qubus\Exception\Exception** |  |





***

### helper



```php
public helper(mixed $name, mixed $args = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |
| `$args` | **mixed** |  |





***

### display



```php
public display(mixed $context = [], mixed $blocks = [], mixed $macros = [], mixed $imports = []): mixed
```




* This method is **abstract**.



**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$context` | **mixed** |  |
| `$blocks` | **mixed** |  |
| `$macros` | **mixed** |  |
| `$imports` | **mixed** |  |





***

### render



```php
public render(mixed $context = [], mixed $blocks = [], mixed $macros = [], mixed $imports = []): bool|string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$context` | **mixed** |  |
| `$blocks` | **mixed** |  |
| `$macros` | **mixed** |  |
| `$imports` | **mixed** |  |





***

### iterate



```php
public iterate(mixed $context, mixed $seq): \Qubus\View\Helper\ContextIterator
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$context` | **mixed** |  |
| `$seq` | **mixed** |  |





***

### getAttr



```php
public getAttr(mixed $obj, mixed $attr, mixed $args = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$obj` | **mixed** |  |
| `$attr` | **mixed** |  |
| `$args` | **mixed** |  |





***

### setAttr



```php
public setAttr(mixed& $obj, mixed $attrs, mixed $value): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$obj` | **mixed** |  |
| `$attrs` | **mixed** |  |
| `$value` | **mixed** |  |





***


***
> Automatically generated on 2025-10-13
