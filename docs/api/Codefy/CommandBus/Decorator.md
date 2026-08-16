# Decorator

***

* Full name: `\Codefy\CommandBus\Decorator`
* Parent interfaces:
  [`\Codefy\CommandBus\CommandBus`](./CommandBus.md)

## Methods

### setInnerBus

Set the CommandBus which we're decorating.

```php
public setInnerBus(\Codefy\CommandBus\CommandBus $bus): void
```

**Parameters:**

| Parameter | Type                              | Description |
|-----------|-----------------------------------|-------------|
| `$bus`    | **\Codefy\CommandBus\CommandBus** |             |

***

## Inherited methods

### execute

Execute a command

```php
public execute(\Codefy\CommandBus\Command $command): mixed
```

**Parameters:**

| Parameter  | Type                           | Description |
|------------|--------------------------------|-------------|
| `$command` | **\Codefy\CommandBus\Command** |             |

***
