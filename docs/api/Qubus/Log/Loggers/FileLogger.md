***

# FileLogger





* Full name: `\Qubus\Log\Loggers\FileLogger`
* Parent class: [`\Qubus\Log\Loggers\BaseLogger`](./BaseLogger.md)
* This class implements:
[`\Psr\Log\LoggerInterface`](../../../Psr/Log/LoggerInterface.md)



## Properties


### filenameFormat

Date format of the log filename.

```php
protected string $filenameFormat
```






***

### filenameExtension

Extension of the log file.

```php
protected string $filenameExtension
```






***

### logFormat



```php
protected ?\Qubus\Log\Format $logFormat
```






***

### logFilename



```php
protected ?\Qubus\Log\Filename $logFilename
```






***

### filesystem



```php
public \League\Flysystem\FilesystemOperator $filesystem
```






***

### threshold



```php
public string|\Psr\Log\LogLevel $threshold
```






***

## Methods


### __construct



```php
public __construct(\League\Flysystem\FilesystemOperator $filesystem, string|\Psr\Log\LogLevel $threshold, array $params = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$filesystem` | **\League\Flysystem\FilesystemOperator** | Flysystem filesystem abstraction |
| `$threshold` | **string&#124;\Psr\Log\LogLevel** | Lowest level of logging to write |
| `$params` | **array** |  |




**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)



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




**Throws:**

- [`FilesystemException`](../../../League/Flysystem/FilesystemException.md)



***

### setFilenameFormat

Set the log filename format using PHP's date parameters.

```php
public setFilenameFormat(string $filenameFormat): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$filenameFormat` | **string** |  |





**See Also:**

* https://secure.php.net/manual/en/function.date.php - 

***

### setFilenameExtension

Set the filename extension. Ex: 'log' will be '.log'.

```php
public setFilenameExtension(string $filenameExtension): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$filenameExtension` | **string** |  |





***

### setLogFormat

Optionally create your own Format class and set it to be used instead.

```php
public setLogFormat(\Qubus\Log\Format $logFormat): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$logFormat` | **\Qubus\Log\Format** |  |





***

### setLogFilename

Optionally create your own Filename class and use this method to use it.

```php
public setLogFilename(\Qubus\Log\Filename $logFilename): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$logFilename` | **\Qubus\Log\Filename** |  |





***


## Inherited methods


### __construct



```php
public __construct(array $params = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$params` | **array** |  |




**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)



***

### isAvailable



```php
public isAvailable(mixed $level): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$level` | **mixed** |  |





***

### getDate



```php
protected getDate(): string
```












***

### stringify



```php
protected stringify(array $data = []): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |





***

### interpolate



```php
protected interpolate(mixed $message, array $context = []): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **mixed** |  |
| `$context` | **array** |  |





***

### __get



```php
public __get(mixed $name): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |




**Throws:**

- [`Exception`](../../Exception/Exception.md)



***

### __set



```php
public __set(mixed $name, mixed $value): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |
| `$value` | **mixed** |  |




**Throws:**

- [`Exception`](../../Exception/Exception.md)



***

### __isset



```php
public __isset(mixed $name): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |





***


***
> Automatically generated on 2025-10-13
