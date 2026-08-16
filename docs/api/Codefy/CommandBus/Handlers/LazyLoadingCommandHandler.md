# LazyLoadingCommandHandler

***

* Full name: `\Codefy\CommandBus\Handlers\LazyLoadingCommandHandler`
* This class implements:
  [`\Codefy\CommandBus\CommandHandler`](../CommandHandler.md)

## Properties

### handlerName

```php
public string $handlerName
```

***

### container

```php
public \Codefy\CommandBus\Container $container
```

***

## Methods

### __construct

```php
public __construct(string $handlerName, \Codefy\CommandBus\Container $container): mixed
```

**Parameters:**

| Parameter      | Type                             | Description |
|----------------|----------------------------------|-------------|
| `$handlerName` | **string**                       |             |
| `$container`   | **\Codefy\CommandBus\Container** |             |

***

### handle

Handle a command execution.

```php
public handle(\Codefy\CommandBus\Command $command): mixed
```

**Parameters:**

| Parameter  | Type                           | Description |
|------------|--------------------------------|-------------|
| `$command` | **\Codefy\CommandBus\Command** |             |

**Throws:**

- [`CommandCouldNotBeHandledException`](../Exceptions/CommandCouldNotBeHandledException.md)

***
