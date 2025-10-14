***

# IfNode





* Full name: `\Qubus\View\Node\IfNode`
* Parent class: [`\Qubus\View\BaseNode`](../BaseNode.md)
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### tests



```php
private $tests
```






***

### else



```php
private $else
```






***

## Methods


### __construct



```php
public __construct(mixed $tests, mixed $else, mixed $line): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$tests` | **mixed** |  |
| `$else` | **mixed** |  |
| `$line` | **mixed** |  |





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


## Inherited methods


### __construct



```php
public __construct(int $line): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$line` | **int** |  |





***

### getLine



```php
public getLine(): int
```












***

### addTraceInfo



```php
public addTraceInfo(mixed $compiler, mixed $indent): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$compiler` | **mixed** |  |
| `$indent` | **mixed** |  |





***

### compile



```php
public compile(mixed $compiler, mixed $indent): mixed
```




* This method is **abstract**.



**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$compiler` | **mixed** |  |
| `$indent` | **mixed** |  |





***


***
> Automatically generated on 2025-10-13
