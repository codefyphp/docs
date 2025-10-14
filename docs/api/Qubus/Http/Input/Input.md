***

# Input





* Full name: `\Qubus\Http\Input\Input`
* This class implements:
[`\Qubus\Http\Input\Item`](./Item.md), [`\ArrayAccess`](../../../ArrayAccess.md), [`\IteratorAggregate`](../../../IteratorAggregate.md)



## Properties


### index



```php
public string|int|null $index
```






***

### name



```php
public ?string $name
```






***

### value



```php
public ?string $value
```






***

## Methods


### __construct



```php
public __construct(string|int $index, ?string $value = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$index` | **string&#124;int** |  |
| `$value` | **?string** |  |





***

### getIndex



```php
public getIndex(): string
```












***

### setIndex



```php
public setIndex(string $index): \Qubus\Http\Input\Item
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$index` | **string** |  |





***

### getName



```php
public getName(): ?string
```












***

### setName

Set input name

```php
public setName(string $name): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### getValue



```php
public getValue(): ?string
```












***

### setValue

Set input value

```php
public setValue(string $value): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **string** |  |





***

### __toString



```php
public __toString(): string
```












***

### offsetExists



```php
public offsetExists(mixed $offset): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **mixed** |  |





***

### offsetGet



```php
public offsetGet(mixed $offset): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **mixed** |  |





***

### offsetSet



```php
public offsetSet(mixed $offset, mixed $value): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **mixed** |  |
| `$value` | **mixed** |  |





***

### offsetUnset



```php
public offsetUnset(mixed $offset): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **mixed** |  |





***

### getIterator



```php
public getIterator(): \Traversable
```












***


***
> Automatically generated on 2025-10-13
