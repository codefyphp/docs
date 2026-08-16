# NativeCommandHandlerResolver

***

* Full name: `\Codefy\CommandBus\Resolvers\NativeCommandHandlerResolver`
* This class implements:
  [`\Codefy\CommandBus\CommandHandlerResolver`](../CommandHandlerResolver.md)

## Properties

### handlers

```php
protected \Codefy\CommandBus\CommandHandler[] $handlers
```

***

### container

```php
protected \Codefy\CommandBus\Container $container
```

***

## Methods

### __construct

```php
public __construct(\Codefy\CommandBus\Container $container = new \Codefy\CommandBus\Containers\NativeContainer()): mixed
```

**Parameters:**

| Parameter    | Type                             | Description |
|--------------|----------------------------------|-------------|
| `$container` | **\Codefy\CommandBus\Container** |             |

***

### resolve

Retrieve a CommandHandler for a given Command

```php
public resolve(\Codefy\CommandBus\Command $command): \Codefy\CommandBus\CommandHandler
```

**Parameters:**

| Parameter  | Type                           | Description |
|------------|--------------------------------|-------------|
| `$command` | **\Codefy\CommandBus\Command** |             |

**Throws:**

- [`UnresolvableCommandHandlerException`](../Exceptions/UnresolvableCommandHandlerException.md)
- [`ReflectionException`](../../../ReflectionException.md)

***

### bindHandler

Bind a handler to a command. These bindings should overrule the default
resolution behavior for this resolver

```php
public bindHandler(string $commandName, callable|\Codefy\CommandBus\CommandHandler|class-string $handler): void
```

**Parameters:**

| Parameter      | Type                                                          | Description |
|----------------|---------------------------------------------------------------|-------------|
| `$commandName` | **string**                                                    |             |
| `$handler`     | **callable\|\Codefy\CommandBus\CommandHandler\|class-string** |             |

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***
