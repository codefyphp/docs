***

# Compiler





* Full name: `\Qubus\View\Compiler`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### result



```php
private string $result
```






***

### module



```php
private \Qubus\View\Module $module
```






***

### line



```php
private int $line
```






***

### trace



```php
private array $trace
```






***

## Methods


### __construct



```php
public __construct(\Qubus\View\Module $module): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$module` | **\Qubus\View\Module** |  |





***

### write



```php
private write(mixed $string): \Qubus\View\Compiler
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **mixed** |  |





***

### raw



```php
public raw(mixed $raw, mixed $indent): \Qubus\View\Compiler
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$raw` | **mixed** |  |
| `$indent` | **mixed** |  |





***

### repr



```php
public repr(mixed $repr, int $indent): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$repr` | **mixed** |  |
| `$indent` | **int** |  |





***

### compile



```php
public compile(): string
```












***

### pushContext



```php
public pushContext(mixed $name, mixed $indent): \Qubus\View\Compiler
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |
| `$indent` | **mixed** |  |





***

### popContext



```php
public popContext(mixed $name, mixed $indent): \Qubus\View\Compiler
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |
| `$indent` | **mixed** |  |





***

### addTraceInfo



```php
public addTraceInfo(\Qubus\View\BaseNode $node, int $indent, bool $line = true): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$node` | **\Qubus\View\BaseNode** |  |
| `$indent` | **int** |  |
| `$line` | **bool** |  |





***

### getTraceInfo



```php
public getTraceInfo(bool $export = false): array|string|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$export` | **bool** |  |





***


***
> Automatically generated on 2025-10-13
