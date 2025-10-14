***

# Logger





* Full name: `\Qubus\Log\Logger`
* Parent class: [`AbstractLogger`](../../Psr/Log/AbstractLogger.md)



## Properties


### loggers



```php
protected \Iterator $loggers
```






***

## Methods


### __construct



```php
public __construct(\Iterator $loggers): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$loggers` | **\Iterator** |  |





***

### log



```php
public log(string|\Psr\Log\LogLevel $level, string|\Stringable $message, array $context = []): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$level` | **string&#124;\Psr\Log\LogLevel** |  |
| `$message` | **string&#124;\Stringable** |  |
| `$context` | **array** |  |





***


***
> Automatically generated on 2025-10-13
