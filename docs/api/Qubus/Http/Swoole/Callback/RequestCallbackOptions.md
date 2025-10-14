***

# RequestCallbackOptions





* Full name: `\Qubus\Http\Swoole\Callback\RequestCallbackOptions`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### responseChunkSize



```php
private int $responseChunkSize
```






***

### streamFactory



```php
private \Psr\Http\Message\StreamFactoryInterface $streamFactory
```






***

## Methods


### create



```php
public static create(): self
```



* This method is **static**.








***

### __construct



```php
public __construct(): mixed
```












***

### getResponseChunkSize



```php
public getResponseChunkSize(): int
```












***

### setResponseChunkSize



```php
public setResponseChunkSize(int $responseChunkSize): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$responseChunkSize` | **int** |  |





***

### getStreamFactory



```php
public getStreamFactory(): \Psr\Http\Message\StreamFactoryInterface
```












***

### setStreamFactory



```php
public setStreamFactory(\Psr\Http\Message\StreamFactoryInterface $streamFactory): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$streamFactory` | **\Psr\Http\Message\StreamFactoryInterface** |  |





***


***
> Automatically generated on 2025-10-13
