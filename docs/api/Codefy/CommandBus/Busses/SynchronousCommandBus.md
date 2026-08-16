# SynchronousCommandBus

***

* Full name: `\Codefy\CommandBus\Busses\SynchronousCommandBus`
* This class implements:
  [`\Codefy\CommandBus\CommandBus`](../CommandBus.md)

## Properties

### resolver

```php
protected \Codefy\CommandBus\CommandHandlerResolver $resolver
```

***

## Methods

### __construct

```php
public __construct(\Codefy\CommandBus\CommandHandlerResolver $resolver = new \Codefy\CommandBus\Resolvers\NativeCommandHandlerResolver()): mixed
```

**Parameters:**

| Parameter   | Type                                          | Description |
|-------------|-----------------------------------------------|-------------|
| `$resolver` | **\Codefy\CommandBus\CommandHandlerResolver** |             |

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

- [`UnresolvableCommandHandlerException`](../Exceptions/UnresolvableCommandHandlerException.md)
- [`ReflectionException`](../../../ReflectionException.md)

***
