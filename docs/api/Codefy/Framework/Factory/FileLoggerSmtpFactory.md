***

# FileLoggerSmtpFactory





* Full name: `\Codefy\Framework\Factory\FileLoggerSmtpFactory`
* This class implements:
[`\Codefy\Framework\Contracts\LoggerFactory`](../Contracts/LoggerFactory.md)




## Methods


### getLogger



```php
public static getLogger(): \Psr\Log\LoggerInterface
```



* This method is **static**.







**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***


## Inherited methods


### emergency

System is unusable.

```php
public static emergency(string|\Stringable $message, array $context = []): void
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string&#124;\Stringable** |  |
| `$context` | **array** |  |




**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)

- [`ReflectionException`](../../../ReflectionException.md)



***

### alert

Action must be taken immediately.

```php
public static alert(string|\Stringable $message, array $context = []): void
```

Example: Entire website down, database unavailable, etc. This should
trigger the SMS alerts and wake you up.

* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string&#124;\Stringable** |  |
| `$context` | **array** |  |




**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)

- [`ReflectionException`](../../../ReflectionException.md)



***

### critical

Critical conditions.

```php
public static critical(string|\Stringable $message, array $context = []): void
```

Example: Application component unavailable, unexpected exception.

* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string&#124;\Stringable** |  |
| `$context` | **array** |  |




**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)

- [`ReflectionException`](../../../ReflectionException.md)



***

### error

Runtime errors that do not require immediate action but should typically
be logged and monitored.

```php
public static error(string|\Stringable $message, array $context = []): void
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string&#124;\Stringable** |  |
| `$context` | **array** |  |




**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)

- [`ReflectionException`](../../../ReflectionException.md)



***

### warning

Exceptional occurrences that are not errors.

```php
public static warning(string|\Stringable $message, array $context = []): void
```

Example: Use of deprecated APIs, poor use of an API, undesirable things
that are not necessarily wrong.

* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string&#124;\Stringable** |  |
| `$context` | **array** |  |




**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)

- [`ReflectionException`](../../../ReflectionException.md)



***

### notice

Normal but significant events.

```php
public static notice(string|\Stringable $message, array $context = []): void
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string&#124;\Stringable** |  |
| `$context` | **array** |  |




**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)

- [`ReflectionException`](../../../ReflectionException.md)



***

### info

Interesting events.

```php
public static info(string|\Stringable $message, array $context = []): void
```

Example: User logs in, SQL logs.

* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string&#124;\Stringable** |  |
| `$context` | **array** |  |




**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)

- [`ReflectionException`](../../../ReflectionException.md)



***

### debug

Detailed debug information.

```php
public static debug(string|\Stringable $message, array $context = []): void
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string&#124;\Stringable** |  |
| `$context` | **array** |  |




**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)

- [`ReflectionException`](../../../ReflectionException.md)



***


***
> Automatically generated on 2025-10-13
