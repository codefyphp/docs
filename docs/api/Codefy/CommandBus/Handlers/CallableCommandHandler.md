# CallableCommandHandler

***

* Full name: `\Codefy\CommandBus\Handlers\CallableCommandHandler`
* This class implements:
  [`\Codefy\CommandBus\CommandHandler`](../CommandHandler.md)

## Properties

### handler

```php
protected callable $handler
```

***

## Methods

### __construct

```php
public __construct(callable $handler): mixed
```

**Parameters:**

| Parameter  | Type         | Description |
|------------|--------------|-------------|
| `$handler` | **callable** |             |

***

### handle

Handle a command execution

```php
public handle(\Codefy\CommandBus\Command $command): mixed
```

**Parameters:**

| Parameter  | Type                           | Description |
|------------|--------------------------------|-------------|
| `$command` | **\Codefy\CommandBus\Command** |             |

***
