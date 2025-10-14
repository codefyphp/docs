***

# ArrayExtra





* Full name: `\Qubus\NoSql\ArrayExtra`
* This class implements:
[`\ArrayAccess`](../../ArrayAccess.md)



## Properties


### items



```php
protected array $items
```






***

## Methods


### __construct

Constructor

```php
public __construct(array $items): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$items` | **array** |  |





***

### arrayHas

Check if an item or items exist in an array using "dot" notation.

```php
public static arrayHas(array $array, string|int $key): bool
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** |  |
| `$key` | **string&#124;int** |  |





***

### arrayGet

Get an item from an array using "dot" notation.

```php
public static arrayGet(array $array, string $key = null): mixed
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** |  |
| `$key` | **string** |  |





***

### arraySet

Set an item on an array or object using dot notation.

```php
public static arraySet(mixed& $target, array|string $key, mixed $value, bool $overwrite = true): mixed
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$target` | **mixed** |  |
| `$key` | **array&#124;string** |  |
| `$value` | **mixed** |  |
| `$overwrite` | **bool** |  |





***

### arrayRemove

Remove item in array.

```php
public static arrayRemove(array& $array, string $key): void
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** |  |
| `$key` | **string** |  |





***

### merge

Merge array.

```php
public merge(array $value): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **array** |  |





***

### getArrayValue

Returns array value.

```php
protected getArrayValue(array|\Qubus\NoSql\ArrayExtra $value, string $message): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **array&#124;\Qubus\NoSql\ArrayExtra** |  |
| `$message` | **string** |  |





***

### toArray

Array items.

```php
public toArray(): array
```












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

### offsetExists



```php
public offsetExists(mixed $offset): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **mixed** |  |





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

### offsetGet



```php
public offsetGet(mixed $offset): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **mixed** |  |





***


***
> Automatically generated on 2025-10-13
