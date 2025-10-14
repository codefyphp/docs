***

# Dispatcher





* Full name: `\Qubus\EventDispatcher\Legacy\Dispatcher`
* This class implements:
[`\Qubus\EventDispatcher\Legacy\EventDispatcher`](./EventDispatcher.md)



## Properties


### listeners

Array of listeners.

```php
protected \Qubus\EventDispatcher\Legacy\ListenerPriorityQueue[] $listeners
```






***

## Methods


### dispatch

Dispatches an event to all registered listeners.

```php
public dispatch(\Qubus\EventDispatcher\Legacy\Event|string $eventName, ?\Qubus\EventDispatcher\Legacy\Event $event = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventName` | **\Qubus\EventDispatcher\Legacy\Event&#124;string** |  |
| `$event` | **?\Qubus\EventDispatcher\Legacy\Event** |  |





***

### addListener

Registries a listener for the event.

```php
public addListener(string $eventName, callable|\Qubus\EventDispatcher\Legacy\EventListener $listener, int $priority = self::PRIORITY_DEFAULT): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventName` | **string** |  |
| `$listener` | **callable&#124;\Qubus\EventDispatcher\Legacy\EventListener** |  |
| `$priority` | **int** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### addSubscriber

Registries a subscriber.

```php
public addSubscriber(\Qubus\EventDispatcher\Legacy\EventSubscriber $subscriber): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$subscriber` | **\Qubus\EventDispatcher\Legacy\EventSubscriber** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### removeListener

Removes a listener from the specified event.

```php
public removeListener(string $eventName, callable|\Qubus\EventDispatcher\Legacy\EventListener $listener): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventName` | **string** |  |
| `$listener` | **callable&#124;\Qubus\EventDispatcher\Legacy\EventListener** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### removeSubscriber

Removes a subscriber.

```php
public removeSubscriber(\Qubus\EventDispatcher\Legacy\EventSubscriber $subscriber): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$subscriber` | **\Qubus\EventDispatcher\Legacy\EventSubscriber** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### removeAllListeners

Removes all listeners from the specified event.

```php
public removeAllListeners(?string $eventName = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventName` | **?string** |  |





***

### hasListener

Checks whether the listener is existed for the event.

```php
public hasListener(string $eventName, callable|\Qubus\EventDispatcher\Legacy\EventListener $listener): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventName` | **string** |  |
| `$listener` | **callable&#124;\Qubus\EventDispatcher\Legacy\EventListener** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### getListeners

Gets all listeners of the event or all registered listeners.

```php
public getListeners(?string $eventName = null): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventName` | **?string** |  |





***


***
> Automatically generated on 2025-10-13
