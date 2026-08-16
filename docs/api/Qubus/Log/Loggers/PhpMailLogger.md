# PhpMailLogger

***

* Full name: `\Qubus\Log\Loggers\PhpMailLogger`
* Parent class: [`\Qubus\Log\Loggers\BaseLogger`](./BaseLogger.md)
* This class implements:
  `LoggerInterface`

## Properties

### subject

```php
public string $subject
```

***

### maxColumn

```php
public int $maxColumn
```

***

### to

```php
protected string|array $to
```

***

### headers

```php
protected array $headers
```

***

### parameters

```php
protected array $parameters
```

***

### contentType

```php
protected string $contentType
```

***

### encoding

```php
protected string $encoding
```

***

### from

```php
protected string $from
```

***

### logFormat

```php
protected ?\Qubus\Log\Format $logFormat
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
public __construct(string|\Psr\Log\LogLevel $threshold, array $params = []): mixed
```

**Parameters:**

| Parameter    | Type                          | Description                       |
|--------------|-------------------------------|-----------------------------------|
| `$threshold` | **string\|\Psr\Log\LogLevel** | Lowest level of logging to write. |
| `$params`    | **array**                     |                                   |

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

***

### log

```php
public log(string|\Psr\Log\LogLevel $level, string|\Stringable $message, array $context = []): void
```

**Parameters:**

| Parameter  | Type                          | Description |
|------------|-------------------------------|-------------|
| `$level`   | **string\|\Psr\Log\LogLevel** |             |
| `$message` | **string\|\Stringable**       |             |
| `$context` | **array**                     |             |

***

### send

```php
protected send(mixed $content): void
```

**Parameters:**

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `$content` | **mixed** |             |

***

### setHeader

```php
public setHeader(array $headers): $this
```

**Parameters:**

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `$headers` | **array** |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***

### setParameter

```php
public setParameter(array|string $parameters): $this
```

**Parameters:**

| Parameter     | Type              | Description |
|---------------|-------------------|-------------|
| `$parameters` | **array\|string** |             |

***

### setContentType

```php
public setContentType(string $contentType): $this
```

**Parameters:**

| Parameter      | Type       | Description |
|----------------|------------|-------------|
| `$contentType` | **string** |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***

### getContentType

```php
public getContentType(): mixed
```

***

### setEncoding

```php
public setEncoding(string $encoding): $this
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$encoding` | **string** |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***

### getEncoding

```php
public getEncoding(): string
```

***

### setTo

```php
public setTo(array|string $value): void
```

**Parameters:**

| Parameter | Type              | Description |
|-----------|-------------------|-------------|
| `$value`  | **array\|string** |             |

***

### setFrom

```php
public setFrom(string $value): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$value`  | **string** |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***

### isHtml

```php
protected isHtml(array $data): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **array** |             |

***

## Inherited methods

### __construct

```php
public __construct(array $params = []): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$params` | **array** |             |

**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)

***

### isAvailable

```php
public isAvailable(mixed $level): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$level`  | **mixed** |             |

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

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **array** |             |

***

### interpolate

```php
protected interpolate(mixed $message, array $context = []): string
```

**Parameters:**

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `$message` | **mixed** |             |
| `$context` | **array** |             |

***

### __get

```php
public __get(mixed $name): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$name`   | **mixed** |             |

**Throws:**

- [`Exception`](../../Exception/Exception.md)

***

### __set

```php
public __set(mixed $name, mixed $value): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$name`   | **mixed** |             |
| `$value`  | **mixed** |             |

**Throws:**

- [`Exception`](../../Exception/Exception.md)

***

### __isset

```php
public __isset(mixed $name): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$name`   | **mixed** |             |

***
