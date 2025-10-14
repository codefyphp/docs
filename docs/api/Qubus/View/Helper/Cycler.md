***

# Cycler





* Full name: `\Qubus\View\Helper\Cycler`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\IteratorAggregate`](../../../IteratorAggregate.md)
* This class is a **Final class**



## Properties


### elements



```php
private array $elements
```






***

### length



```php
private ?int $length
```






***

### idx



```php
private int $idx
```






***

## Methods


### __construct



```php
public __construct(array $elements): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$elements` | **array** |  |





***

### getIterator



```php
public getIterator(): \ArrayIterator
```












***

### next



```php
public next(): mixed
```












***

### random



```php
public random(mixed $seed = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$seed` | **mixed** |  |





***

### count



```php
public count(): int
```












***

### cycle



```php
public cycle(): float
```












***


***
> Automatically generated on 2025-10-13
