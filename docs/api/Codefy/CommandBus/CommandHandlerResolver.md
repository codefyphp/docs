# CommandHandlerResolver

***

* Full name: `\Codefy\CommandBus\CommandHandlerResolver`

## Methods

### resolve

Retrieve a CommandHandler for a given Command.

```php
public resolve(\Codefy\CommandBus\Command $command): \Codefy\CommandBus\CommandHandler
```

**Parameters:**

| Parameter  | Type                           | Description |
|------------|--------------------------------|-------------|
| `$command` | **\Codefy\CommandBus\Command** |             |

***

### bindHandler

Bind a handler to a command. These bindings should overrule the default
resolution behavior for this resolver.

```php
public bindHandler(string $commandName, \Codefy\CommandBus\CommandHandler|callable|string $handler): void
```

**Parameters:**

| Parameter      | Type                                                    | Description |
|----------------|---------------------------------------------------------|-------------|
| `$commandName` | **string**                                              |             |
| `$handler`     | **\Codefy\CommandBus\CommandHandler\|callable\|string** |             |

***
