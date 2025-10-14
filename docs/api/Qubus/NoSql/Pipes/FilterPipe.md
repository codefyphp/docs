***

# FilterPipe





* Full name: `\Qubus\NoSql\Pipes\FilterPipe`
* This class implements:
[`\Qubus\NoSql\Pipes\Pipe`](./Pipe.md)



## Properties


### filters



```php
protected array $filters
```






***

## Methods


### process



```php
public process(array $data): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### add



```php
public add(\Closure $filter, string $type = &#039;AND&#039;): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$filter` | **\Closure** |  |
| `$type` | **string** |  |





***


***
> Automatically generated on 2025-10-13
