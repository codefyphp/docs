***

# ContextIterator





* Full name: `\Qubus\View\Helper\ContextIterator`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Iterator`](../../../Iterator.md)
* This class is a **Final class**



## Properties


### sequence



```php
private \ArrayIterator|\Traversable|\Countable $sequence
```






***

### length



```php
private ?int $length
```






***

### parent



```php
private mixed $parent
```






***

### index



```php
private int $index
```






***

### count



```php
private int $count
```






***

### first



```php
private bool $first
```






***

### last



```php
private bool $last
```






***

## Methods


### __construct



```php
public __construct(mixed $sequence, mixed $parent): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$sequence` | **mixed** |  |
| `$parent` | **mixed** |  |





***

### rewind



```php
public rewind(): void
```












***

### key



```php
public key(): mixed
```












***

### valid



```php
public valid(): bool
```












***

### next



```php
public next(): void
```












***

### current



```php
public current(): mixed
```












***


***
> Automatically generated on 2025-10-13
