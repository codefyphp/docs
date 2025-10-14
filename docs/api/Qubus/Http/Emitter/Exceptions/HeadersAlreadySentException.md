***

# HeadersAlreadySentException





* Full name: `\Qubus\Http\Emitter\Exceptions\HeadersAlreadySentException`
* Parent class: [`\Qubus\Http\Emitter\Exceptions\EmitterException`](./EmitterException.md)



## Properties


### headersSentFile



```php
public string $headersSentFile
```






***

### headersSentLine



```php
public int $headersSentLine
```






***

## Methods


### __construct



```php
public __construct(string $headersSentFile, int $headersSentLine, int $code, null|\Throwable $previous = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$headersSentFile` | **string** | PHP source file name where output started in |
| `$headersSentLine` | **int** | Line number in the PHP source file name where<br />output started in |
| `$code` | **int** |  |
| `$previous` | **null&#124;\Throwable** |  |





***


***
> Automatically generated on 2025-10-13
