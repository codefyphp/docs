***

# EventDispatchingDecorator





* Full name: `\Codefy\CommandBus\Decorators\EventDispatchingDecorator`
* This class implements:
[`\Codefy\CommandBus\Decorator`](../Decorator.md)



## Properties


### dispatcher



```php
protected \Codefy\CommandBus\Decorators\EventDispatcher $dispatcher
```






***

### innerCommandBus



```php
protected ?\Codefy\CommandBus\CommandBus $innerCommandBus
```






***

## Methods


### __construct



```php
public __construct(\Codefy\CommandBus\Decorators\EventDispatcher $dispatcher, ?\Codefy\CommandBus\CommandBus $innerCommandBus = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$dispatcher` | **\Codefy\CommandBus\Decorators\EventDispatcher** |  |
| `$innerCommandBus` | **?\Codefy\CommandBus\CommandBus** |  |





***

### setInnerBus

Set the CommandBus which we're decorating.

```php
public setInnerBus(\Codefy\CommandBus\CommandBus $bus): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$bus` | **\Codefy\CommandBus\CommandBus** |  |





***

### execute

Execute a command and dispatch and event.

```php
public execute(\Codefy\CommandBus\Command $command): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$command` | **\Codefy\CommandBus\Command** |  |




**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)



***

### getEventName

Get the event name for a given Command.

```php
protected getEventName(\Codefy\CommandBus\Command $command): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$command` | **\Codefy\CommandBus\Command** |  |





***


***
> Automatically generated on 2025-10-13
