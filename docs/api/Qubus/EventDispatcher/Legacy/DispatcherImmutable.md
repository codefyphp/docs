***

# DispatcherImmutable





* Full name: `\Qubus\EventDispatcher\Legacy\DispatcherImmutable`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Qubus\EventDispatcher\Legacy\EventDispatcher`](./EventDispatcher.md)
* This class is a **Final class**



## Properties


### dispatcher



```php
private \Qubus\EventDispatcher\Legacy\EventDispatcher $dispatcher
```






***

## Methods


### __construct



```php
public __construct(\Qubus\EventDispatcher\Legacy\EventDispatcher $dispatcher): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$dispatcher` | **\Qubus\EventDispatcher\Legacy\EventDispatcher** |  |





***

### dispatch

Dispatches an event to all registered listeners.

```php
public dispatch(\Qubus\EventDispatcher\Legacy\Event|string $eventName, ?\Qubus\EventDispatcher\Legacy\Event $event = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventName` | **\Qubus\EventDispatcher\Legacy\Event&#124;string** |  |
| `$event` | **?\Qubus\EventDispatcher\Legacy\Event** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### addListener

Registries a listener for the event.

```php
public addListener(string $eventName, callable|\Qubus\EventDispatcher\Legacy\EventListener $listener, int $priority = self::PRIORITY_DEFAULT): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventName` | **string** |  |
| `$listener` | **callable&#124;\Qubus\EventDispatcher\Legacy\EventListener** |  |
| `$priority` | **int** |  |





***

### addSubscriber

Registries a subscriber.

```php
public addSubscriber(\Qubus\EventDispatcher\Legacy\EventSubscriber $subscriber): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$subscriber` | **\Qubus\EventDispatcher\Legacy\EventSubscriber** |  |





***

### removeListener

Removes a listener from the specified event.

```php
public removeListener(string $eventName, callable|\Qubus\EventDispatcher\Legacy\EventListener $listener): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventName` | **string** |  |
| `$listener` | **callable&#124;\Qubus\EventDispatcher\Legacy\EventListener** |  |





***

### removeSubscriber

Removes a subscriber.

```php
public removeSubscriber(\Qubus\EventDispatcher\Legacy\EventSubscriber $subscriber): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$subscriber` | **\Qubus\EventDispatcher\Legacy\EventSubscriber** |  |





***

### removeAllListeners

Removes all listeners from the specified event.

```php
public removeAllListeners(?string $eventName = null): mixed
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
