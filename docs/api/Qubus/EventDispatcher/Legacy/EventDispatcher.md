***

# EventDispatcher





* Full name: `\Qubus\EventDispatcher\Legacy\EventDispatcher`


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`PRIORITY_LOW`|public|int|-100|
|`PRIORITY_DEFAULT`|public|int|0|
|`PRIORITY_HIGH`|public|int|100|

## Methods


### dispatch

Dispatches an event to all registered listeners.

```php
public dispatch(string|\Qubus\EventDispatcher\Legacy\Event $eventName, \Qubus\EventDispatcher\Legacy\Event|null $event = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventName` | **string&#124;\Qubus\EventDispatcher\Legacy\Event** |  |
| `$event` | **\Qubus\EventDispatcher\Legacy\Event&#124;null** |  |





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
public getListeners(string|null $eventName = null): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventName` | **string&#124;null** |  |





***


***
> Automatically generated on 2025-10-13
