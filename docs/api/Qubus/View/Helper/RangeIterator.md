***

# RangeIterator





* Full name: `\Qubus\View\Helper\RangeIterator`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Iterator`](../../../Iterator.md)
* This class is a **Final class**



## Properties


### lower



```php
private float|int $lower
```






***

### upper



```php
private float|int $upper
```






***

### step



```php
private float|int $step
```






***

### current



```php
private float|int $current
```






***

## Methods


### __construct



```php
public __construct(float|int $lower, float|int $upper, float|int $step = 1): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$lower` | **float&#124;int** |  |
| `$upper` | **float&#124;int** |  |
| `$step` | **float&#124;int** |  |





***

### length



```php
public length(): float|int
```












***

### includes



```php
public includes(mixed $n): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$n` | **mixed** |  |





***

### random



```php
public random(mixed $seed = null): int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$seed` | **mixed** |  |





***

### rewind



```php
public rewind(): void
```












***

### key



```php
public key(): int
```












***

### valid



```php
public valid(): bool
```












***

### next



```php
public next(): \Qubus\View\Helper\RangeIterator
```












***

### current



```php
public current(): int|float
```












***


***
> Automatically generated on 2025-10-13
