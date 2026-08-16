# LoggingDecorator

***

* Full name: `\Codefy\CommandBus\Decorators\LoggingDecorator`
* This class implements:
  [`\Codefy\CommandBus\Decorator`](../Decorator.md)

## Properties

### logger

```php
protected \Psr\Log\LoggerInterface $logger
```

***

### context

```php
protected mixed $context
```

***

## Methods

### __construct

```php
public __construct(\Psr\Log\LoggerInterface $logger, mixed|null $context = null, ?\Codefy\CommandBus\CommandBus $innerCommandBus = null): mixed
```

**Parameters:**

| Parameter          | Type                               | Description                                                                                                              |
|--------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| `$logger`          | **\Psr\Log\LoggerInterface**       |                                                                                                                          |
| `$context`         | **mixed\|null**                    | Something which is serializable that will be logged with
the command execution, such as the request/session information. |
| `$innerCommandBus` | **?\Codefy\CommandBus\CommandBus** |                                                                                                                          |

***

### execute

Execute a command.

```php
public execute(\Codefy\CommandBus\Command $command): mixed
```

**Parameters:**

| Parameter  | Type                           | Description |
|------------|--------------------------------|-------------|
| `$command` | **\Codefy\CommandBus\Command** |             |

**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)

***

### log

```php
protected log(string|\Stringable $message, \Codefy\CommandBus\Command $command): void
```

**Parameters:**

| Parameter  | Type                           | Description |
|------------|--------------------------------|-------------|
| `$message` | **string\|\Stringable**        |             |
| `$command` | **\Codefy\CommandBus\Command** |             |

***

### createExceptionString

```php
protected createExceptionString(\Qubus\Exception\Exception $e): string
```

**Parameters:**

| Parameter | Type                           | Description |
|-----------|--------------------------------|-------------|
| `$e`      | **\Qubus\Exception\Exception** |             |

***

## Inherited methods

### setInnerBus

```php
public setInnerBus(\Codefy\CommandBus\CommandBus $bus): void
```

**Parameters:**

| Parameter | Type                              | Description |
|-----------|-----------------------------------|-------------|
| `$bus`    | **\Codefy\CommandBus\CommandBus** |             |

***
