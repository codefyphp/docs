***

# CommandQueueingDecorator

Queue commands which implement QueueableCommand into a CommandQueuer.



* Full name: `\Codefy\CommandBus\Decorators\CommandQueueingDecorator`
* This class implements:
[`\Codefy\CommandBus\Decorator`](../Decorator.md)



## Properties


### queuer



```php
protected \Codefy\CommandBus\CommandQueuer $queuer
```






***

## Methods


### __construct



```php
public __construct(\Codefy\CommandBus\CommandQueuer $queuer, ?\Codefy\CommandBus\CommandBus $innerCommandBus = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$queuer` | **\Codefy\CommandBus\CommandQueuer** |  |
| `$innerCommandBus` | **?\Codefy\CommandBus\CommandBus** |  |





***

### execute

Execute a command.

```php
public execute(\Codefy\CommandBus\Command $command): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$command` | **\Codefy\CommandBus\Command** |  |





***


## Inherited methods


### setInnerBus



```php
public setInnerBus(\Codefy\CommandBus\CommandBus $bus): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$bus` | **\Codefy\CommandBus\CommandBus** |  |





***


***
> Automatically generated on 2025-10-13
