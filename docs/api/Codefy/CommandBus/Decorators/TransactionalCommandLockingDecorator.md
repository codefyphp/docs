***

# TransactionalCommandLockingDecorator

TransactionalCommandLockingDecorator treats commands as transactions. Meaning that any
subsequent Commands passed to the bus from inside the relevant CommandHandler
will not be executed until the initial command is completed.



* Full name: `\Codefy\CommandBus\Decorators\TransactionalCommandLockingDecorator`
* This class implements:
[`\Codefy\CommandBus\Decorator`](../Decorator.md)



## Properties


### locked

Whether a Command is in progress and the bus is locked.

```php
protected bool $locked
```






***

### queue

Queued Commands to be executed when the current command finishes.

```php
protected array $queue
```






***

## Methods


### __construct



```php
public __construct(?\Codefy\CommandBus\CommandBus $innerCommandBus = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$innerCommandBus` | **?\Codefy\CommandBus\CommandBus** |  |





***

### execute

Execute a command

```php
public execute(\Codefy\CommandBus\Command $command): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$command` | **\Codefy\CommandBus\Command** |  |





***

### executeIgnoringLock

Execute a command, regardless of the lock

```php
protected executeIgnoringLock(\Codefy\CommandBus\Command $command): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$command` | **\Codefy\CommandBus\Command** |  |





***

### executeQueue

Execute all queued commands

```php
protected executeQueue(): void
```












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
