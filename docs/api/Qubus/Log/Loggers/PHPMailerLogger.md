***

# PHPMailerLogger





* Full name: `\Qubus\Log\Loggers\PHPMailerLogger`
* Parent class: [`\Qubus\Log\Loggers\BaseLogger`](./BaseLogger.md)
* This class implements:
[`\Psr\Log\LoggerInterface`](../../../Psr/Log/LoggerInterface.md)



## Properties


### subject



```php
public ?string $subject
```






***

### to



```php
protected string|array $to
```






***

### from



```php
protected string $from
```






***

### encoding



```php
protected string $encoding
```






***

### logFormat



```php
protected ?\Qubus\Log\Format $logFormat
```






***

### mailer



```php
public \Qubus\Mail\Mailer $mailer
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
public __construct(\Qubus\Mail\Mailer $mailer, string|\Psr\Log\LogLevel $threshold, array $params = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$mailer` | **\Qubus\Mail\Mailer** |  |
| `$threshold` | **string&#124;\Psr\Log\LogLevel** |  |
| `$params` | **array** |  |





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

### send



```php
protected send(mixed $content): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$content` | **mixed** |  |




**Throws:**

- [`Exception`](../../../PHPMailer/PHPMailer/Exception.md)

- [`Exception`](../../Exception/Exception.md)



***

### setEncoding



```php
public setEncoding(string $encoding): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$encoding` | **string** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### getEncoding



```php
public getEncoding(): string
```












***

### setFrom



```php
public setFrom(mixed $value): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **mixed** |  |





***

### setTo



```php
public setTo(mixed $value): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **mixed** |  |





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
