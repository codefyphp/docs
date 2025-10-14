***

# RoutingEventHandler





* Full name: `\Qubus\Routing\Events\RoutingEventHandler`
* This class implements:
[`\Qubus\Routing\Events\EventHandler`](./EventHandler.md)


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`EVENT_ALL`|public| |&#039;*&#039;|
|`EVENT_INIT`|public| |&#039;onInit&#039;|
|`EVENT_LOAD`|public| |&#039;onLoad&#039;|
|`EVENT_ADD_ROUTE`|public| |&#039;onAddRoute&#039;|
|`EVENT_BOOT`|public| |&#039;onBoot&#039;|
|`EVENT_RENDER_BOOTMANAGER`|public| |&#039;onRenderBootManager&#039;|
|`EVENT_LOAD_ROUTES`|public| |&#039;onLoadRoutes&#039;|
|`EVENT_FIND_ROUTE`|public| |&#039;onFindRoute&#039;|
|`EVENT_GET_URL`|public| |&#039;onGetUrl&#039;|
|`EVENT_MATCH_ROUTE`|public| |&#039;onMatchRoute&#039;|
|`EVENT_RENDER_MIDDLEWARES`|public| |&#039;onRenderMiddlewares&#039;|

## Properties


### events

All available events

```php
public static array $events
```



* This property is **static**.


***

### registeredEvents

List of all registered events.

```php
private array $registeredEvents
```






***

## Methods


### register

Register new event.

```php
public register(string $name, \Closure $callback): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$callback` | **\Closure** |  |





***

### getEvents

Get events.

```php
public getEvents(string|null $name = null, array $names): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string&#124;null** | Filter events by name. |
| `$names` | **array** | Add multiple names... |





***

### fireEvents

Fires any events registered with given event-name

```php
public fireEvents(\Qubus\Routing\Router $router, string $name, array $eventArgs = []): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$router` | **\Qubus\Routing\Router** | Router instance |
| `$name` | **string** | Event name |
| `$eventArgs` | **array** | Event arguments |





***


***
> Automatically generated on 2025-10-13
