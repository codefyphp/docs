***

# InjectionChain





* Full name: `\Qubus\Injector\InjectionChain`



## Properties


### chain

Store the chain of instantiations.

```php
private array $chain
```






***

## Methods


### __construct

Instantiate an InjectionChain object.

```php
public __construct(array $inProgressMakes = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$inProgressMakes` | **array** | Optional. Array of instantiations. |





***

### getChain

Get the chain of instantiations.

```php
public getChain(): array
```









**Return Value:**

Array of instantiations.




***

### getByIndex

Get the instantiation at a specific index.

```php
public getByIndex(int $index): string|false
```

The first (root) instantiation is 0, with each subsequent level adding 1
more to the index.

Provide a negative index to step back from the end of the chain.
Example: `getByIndex( -2 )` will return the second-to-last element.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$index` | **int** | Element index to retrieve. Negative value to fetch from the end of the chain. |


**Return Value:**

Class name of the element at the specified index. False if index not found.



**Throws:**
<p>If the index is not a numeric value.</p>

- [`RuntimeException`](../../RuntimeException.md)



***


***
> Automatically generated on 2025-10-13
