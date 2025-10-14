***

# Token





* Full name: `\Qubus\View\Token`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`EOF`|public| |-1|
|`TEXT`|public| |0|
|`BLOCK_BEGIN`|public| |1|
|`OUTPUT_BEGIN`|public| |2|
|`RAW_BEGIN`|public| |3|
|`BLOCK_END`|public| |4|
|`OUTPUT_END`|public| |5|
|`RAW_END`|public| |6|
|`NAME`|public| |7|
|`NUMBER`|public| |8|
|`STRING`|public| |9|
|`OPERATOR`|public| |10|
|`CONSTANT`|public| |11|

## Properties


### type



```php
public int $type
```






***

### value



```php
public ?string $value
```






***

### line



```php
public int $line
```






***

### char



```php
public int $char
```






***

## Methods


### __construct



```php
public __construct(int $type, ?string $value, int $line, int $char): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$type` | **int** |  |
| `$value` | **?string** |  |
| `$line` | **int** |  |
| `$char` | **int** |  |





***

### getTypeError



```php
public static getTypeError(mixed $type): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$type` | **mixed** |  |





***

### test



```php
public test(mixed $type, mixed $values = null): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$type` | **mixed** |  |
| `$values` | **mixed** |  |





***

### __toString



```php
public __toString(): string
```












***


***
> Automatically generated on 2025-10-13
