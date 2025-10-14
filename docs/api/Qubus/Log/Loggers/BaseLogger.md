***

# BaseLogger





* Full name: `\Qubus\Log\Loggers\BaseLogger`
* Parent class: [`AbstractLogger`](../../../Psr/Log/AbstractLogger.md)
* This class is an **Abstract class**



## Properties


### enabled



```php
public bool $enabled
```






***

### dateFormat



```php
public string $dateFormat
```






***

### levels

Associative array of the log levels that are given a numerical value
to allow comparison of the threshold and the method calling log.

```php
public array $levels
```






***

## Methods


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
