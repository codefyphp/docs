***

# ContentRange





* Full name: `\Qubus\Http\Emitter\ContentRange`



## Properties


### start



```php
private int $start
```






***

### end



```php
private int $end
```






***

### size



```php
private ?int $size
```






***

### unit



```php
private string $unit
```






***

## Methods


### __construct



```php
public __construct(int $start, int $end, null|int $size = null, string $unit = &#039;bytes&#039;): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$start` | **int** | An integer in the given unit indicating the beginning<br />of the request range. |
| `$end` | **int** | An integer in the given unit indicating the end of the<br />requested range. |
| `$size` | **null&#124;int** | The total size of the document. |
| `$unit` | **string** | The unit in which ranges are specified. This is<br />usually `bytes`. |




**Throws:**

- [`EmitterException`](./Exceptions/EmitterException.md)



***

### getUnit

Get the unit in which ranges are specified. This is usually bytes.

```php
public getUnit(): string
```












***

### setUnit

Set the unit in which ranges are specified. This is usually bytes.

```php
public setUnit(string $unit): \Qubus\Http\Emitter\ContentRange
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$unit` | **string** | The unit in which ranges are specified. This is<br />usually bytes. |





***

### getStart

Get the beginning of the request range.

```php
public getStart(): int
```












***

### setStart

Set the beginning of the request range.

```php
public setStart(int $start): \Qubus\Http\Emitter\ContentRange
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$start` | **int** | the beginning of the request range. |




**Throws:**

- [`EmitterException`](./Exceptions/EmitterException.md)



***

### getEnd

Get an integer in the given unit indicating
the end of the requested range.

```php
public getEnd(): int
```












***

### setEnd

Set an integer in the given unit indicating
the end of the requested range.

```php
public setEnd(int $end): \Qubus\Http\Emitter\ContentRange
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$end` | **int** | An integer in the given unit indicating the<br />end of the requested range. |





***

### getSize

Get the total size of the document.

```php
public getSize(): int|null
```












***

### setSize

Set the total size of the document.

```php
public setSize(int|null $size): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$size` | **int&#124;null** | The total size of the document. |





***


***
> Automatically generated on 2025-10-13
