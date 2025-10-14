***

# DatabaseLogger





* Full name: `\Qubus\Log\Loggers\DatabaseLogger`
* Parent class: [`\Qubus\Log\Loggers\BaseLogger`](./BaseLogger.md)
* This class implements:
[`\Psr\Log\LoggerInterface`](../../../Psr/Log/LoggerInterface.md)



## Properties


### table



```php
public ?string $table
```






***

### db



```php
protected ?\PDO $db
```






***

## Methods


### setDb



```php
public setDb(\PDO $value): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **\PDO** |  |





***

### getDb



```php
public getDb(): \PDO
```












***

### log



```php
public log(mixed $level, string|\Stringable $message, array $context = []): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$level` | **mixed** |  |
| `$message` | **string&#124;\Stringable** |  |
| `$context` | **array** |  |





***

### execute



```php
protected execute(array $data): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |





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
