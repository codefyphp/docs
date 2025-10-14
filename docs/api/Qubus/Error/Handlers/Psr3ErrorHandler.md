***

# Psr3ErrorHandler





* Full name: `\Qubus\Error\Handlers\Psr3ErrorHandler`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Qubus\Error\Handlers\ErrorHandler`](./ErrorHandler.md)
* This class is a **Final class**


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`DEFAULT_ERROR_LEVEL_MAP`|private| |[\ParseError::class =&gt; \Psr\Log\LogLevel::CRITICAL, \Throwable::class =&gt; \Psr\Log\LogLevel::ERROR]|
|`DEFAULT_LOG_LEVEL`|private| |\Psr\Log\LogLevel::ERROR|
|`ERROR_KEY`|public| |&#039;error&#039;|

## Properties


### logger



```php
private \Psr\Log\LoggerInterface $logger
```






***

### levelMap

Defines which error levels should be mapped to certain error types.

```php
private array $levelMap
```

Note: The errors are checked in order, so if you want to define fallbacks for classes higher in the tree
make sure to add them to the end of the map.




***

### ignoreSeverity

Ignores the severity when detecting the log level.

```php
private bool $ignoreSeverity
```






***

### allowNonPsrLevels

Enables the handler to accept detecting non-PSR-3 log levels.

```php
private bool $allowNonPsrLevels
```

Note: when detecting an invalid level the handler will silently fall back to the default.




***

## Methods


### __construct



```php
public __construct(\Psr\Log\LoggerInterface $logger, array $levelMap = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$logger` | **\Psr\Log\LoggerInterface** |  |
| `$levelMap` | **array** |  |





***

### ignoreSeverity

Ignores the severity when detecting the log level.

```php
public ignoreSeverity(bool $ignoreSeverity = true): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$ignoreSeverity` | **bool** |  |





***

### allowNonPsrLevels

Enables the handler to accept detecting non-PSR-3 log levels.

```php
public allowNonPsrLevels(bool $allowNonPsrLevels = true): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$allowNonPsrLevels` | **bool** |  |





***

### handle



```php
public handle(\Throwable $t, array $context = []): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$t` | **\Throwable** |  |
| `$context` | **array** |  |





***

### getLevel

Determines the level for the error.

```php
private getLevel(\Throwable $t, array $context): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$t` | **\Throwable** |  |
| `$context` | **array** |  |





***

### checkLevel

Checks whether a log level exists.

```php
private checkLevel(string $level): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$level` | **string** |  |





***

### validateLevel

Validates whether a log level exists (if non-PSR levels are not allowed).

```php
private validateLevel(string $level): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$level` | **string** |  |





***

### getType

Determines the error type.

```php
private getType(\Throwable $t): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$t` | **\Throwable** |  |





***


***
> Automatically generated on 2025-10-13
