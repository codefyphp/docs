***

# CallableListener





* Full name: `\Qubus\EventDispatcher\Legacy\CallableListener`
* This class implements:
[`\Qubus\EventDispatcher\Legacy\EventListener`](./EventListener.md)



## Properties


### callable

The callable callback.

```php
protected callable $callable
```






***

### listeners

Array of callable-listeners.

```php
protected static array $listeners
```



* This property is **static**.


***

## Methods


### __construct



```php
public __construct(callable $callable): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callable` | **callable** |  |





***

### getCallable

Gets callback.

```php
public getCallable(): callable
```












***

### handle

Handles an event.

```php
public handle(\Qubus\EventDispatcher\Legacy\Event $event): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$event` | **\Qubus\EventDispatcher\Legacy\Event** |  |





***

### createFromCallable

Creates a callable-listener.

```php
public static createFromCallable(callable $callable): \Qubus\EventDispatcher\Legacy\CallableListener
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callable` | **callable** |  |





***

### findByCallable

Finds the listener from the collection by its callable.

```php
public static findByCallable(callable $callable): \Qubus\EventDispatcher\Legacy\CallableListener|false
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callable` | **callable** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### clearListeners

Removes all registered callable-listeners.

```php
public static clearListeners(): void
```



* This method is **static**.








***


***
> Automatically generated on 2025-10-13
