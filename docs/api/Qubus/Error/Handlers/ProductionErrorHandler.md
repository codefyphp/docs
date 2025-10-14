***

# ProductionErrorHandler





* Full name: `\Qubus\Error\Handlers\ProductionErrorHandler`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Qubus\Error\Handlers\ErrorHandler`](./ErrorHandler.md)
* This class is a **Final class**


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`ERROR_HANDLER`|public| |&#039;registerErrorHandler&#039;|
|`EXCEPTION_HANDLER`|public| |&#039;registerExceptionHandler&#039;|
|`SHUTDOWN_HANDLER`|public| |&#039;registerShutdownHandler&#039;|

## Properties


### loggers



```php
private \Psr\Log\LoggerInterface[] $loggers
```






***

### displayErrors



```php
protected bool $displayErrors
```






***

### notifyPsr3Loggers



```php
protected bool $notifyPsr3Loggers
```






***

### notifyNativePhpLog



```php
protected bool $notifyNativePhpLog
```






***

## Methods


### __construct



```php
public __construct(bool $displayErrors = false, bool $notifyPsr3Loggers = false, bool $notifyNativePhpLog = true): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$displayErrors` | **bool** |  |
| `$notifyPsr3Loggers` | **bool** |  |
| `$notifyNativePhpLog` | **bool** |  |





***

### addLogger

Adds a logger to the ExceptionHandler.

```php
public addLogger(\Psr\Log\LoggerInterface $logger): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$logger` | **\Psr\Log\LoggerInterface** |  |





***

### log

Logs an error to PHP's native error_log() and PSR3 loggers.

```php
public log(\Throwable $throwable, bool $isEmergency = false): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$throwable` | **\Throwable** |  |
| `$isEmergency` | **bool** | Used only for uncaught exceptions. |





***

### registerErrorHandler

Converts php notices/warnings/errors to ErrorException and throws it.

```php
public registerErrorHandler(int $errno, string $errstr, string $errfile, int $errline): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$errno` | **int** |  |
| `$errstr` | **string** |  |
| `$errfile` | **string** |  |
| `$errline` | **int** |  |




**Throws:**

- [`ErrorException`](../../../ErrorException.md)



***

### registerExceptionHandler

Handle uncaught exceptions.

```php
public registerExceptionHandler(\Throwable $throwable): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$throwable` | **\Throwable** |  |




**Throws:**

- [`Throwable`](../../../Throwable.md)



***

### registerShutdownHandler

When php shuts down, check if this is caused by a(n) (fatal) error.

```php
public registerShutdownHandler(): void
```

If so convert and catch it to have it processed like the rest of the exceptions.









**Throws:**

- [`Throwable`](../../../Throwable.md)



***

### registerAllHandlers



```php
private registerAllHandlers(): void
```












***

### unregister

De-registers the error handling functions, returning them to their previous state.

```php
public unregister(): void
```












***


***
> Automatically generated on 2025-10-13
