# Odin

The main Odin class is a CommandBus, which is effectively a decorator
around another CommandBus interface.

***

* Full name: `\Codefy\CommandBus\Odin`
* This class implements:
  [`\Codefy\CommandBus\CommandBus`](./CommandBus.md)

## Properties

### bus

```php
protected \Codefy\CommandBus\CommandBus $bus
```

***

## Methods

### __construct

Constructor

```php
public __construct(\Codefy\CommandBus\CommandBus $bus = new \Codefy\CommandBus\Busses\SynchronousCommandBus(), \Codefy\CommandBus\Decorator[] $decorators = []): mixed
```

**Parameters:**

| Parameter     | Type                               | Description                                   |
|---------------|------------------------------------|-----------------------------------------------|
| `$bus`        | **\Codefy\CommandBus\CommandBus**  |                                               |
| `$decorators` | **\Codefy\CommandBus\Decorator[]** | Array of \Codefy\CommandBus\Decorator objects |

***

### pushDecorator

Push a new Decorator on to the stack.

```php
public pushDecorator(\Codefy\CommandBus\Decorator $decorator): void
```

**Parameters:**

| Parameter    | Type                             | Description |
|--------------|----------------------------------|-------------|
| `$decorator` | **\Codefy\CommandBus\Decorator** |             |

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

- [`UnresolvableCommandHandlerException`](./Exceptions/UnresolvableCommandHandlerException.md)
- [`ReflectionException`](../../ReflectionException.md)

***
