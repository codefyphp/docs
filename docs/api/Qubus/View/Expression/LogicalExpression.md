***

# LogicalExpression





* Full name: `\Qubus\View\Expression\LogicalExpression`
* Parent class: [`\Qubus\View\Expression\BinaryExpression`](./BinaryExpression.md)
* This class is an **Abstract class**






## Inherited methods


### __construct



```php
public __construct(mixed $left, mixed $right, int $line): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$left` | **mixed** |  |
| `$right` | **mixed** |  |
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
public compile(mixed $compiler, mixed $indent): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$compiler` | **mixed** |  |
| `$indent` | **mixed** |  |





***

### getLeftOperand



```php
public getLeftOperand(): mixed
```












***

### getRightOperand



```php
public getRightOperand(): mixed
```












***

### operator



```php
public operator(): string
```




* This method is **abstract**.







***


***
> Automatically generated on 2025-10-13
