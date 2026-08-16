# RoutingEventHandler

***

* Full name: `\Qubus\Routing\Events\RoutingEventHandler`
* This class implements:
  [`\Qubus\Routing\Events\EventHandler`](./EventHandler.md)

## Constants

| Constant                   | Visibility | Type | Value                 |
|----------------------------|------------|------|-----------------------|
| `EVENT_ALL`                | public     |      | '*'                   |
| `EVENT_INIT`               | public     |      | 'onInit'              |
| `EVENT_LOAD`               | public     |      | 'onLoad'              |
| `EVENT_ADD_ROUTE`          | public     |      | 'onAddRoute'          |
| `EVENT_BOOT`               | public     |      | 'onBoot'              |
| `EVENT_RENDER_BOOTMANAGER` | public     |      | 'onRenderBootManager' |
| `EVENT_LOAD_ROUTES`        | public     |      | 'onLoadRoutes'        |
| `EVENT_FIND_ROUTE`         | public     |      | 'onFindRoute'         |
| `EVENT_GET_URL`            | public     |      | 'onGetUrl'            |
| `EVENT_MATCH_ROUTE`        | public     |      | 'onMatchRoute'        |
| `EVENT_RENDER_MIDDLEWARES` | public     |      | 'onRenderMiddlewares' |

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

| Parameter   | Type         | Description |
|-------------|--------------|-------------|
| `$name`     | **string**   |             |
| `$callback` | **\Closure** |             |

***

### getEvents

Get events.

```php
public getEvents(string|null $name = null, array $names): array
```

**Parameters:**

| Parameter | Type             | Description            |
|-----------|------------------|------------------------|
| `$name`   | **string\|null** | Filter events by name. |
| `$names`  | **array**        | Add multiple names...  |

***

### fireEvents

Fires any events registered with given event-name

```php
public fireEvents(\Qubus\Routing\Router $router, string $name, array $eventArgs = []): void
```

**Parameters:**

| Parameter    | Type                      | Description     |
|--------------|---------------------------|-----------------|
| `$router`    | **\Qubus\Routing\Router** | Router instance |
| `$name`      | **string**                | Event name      |
| `$eventArgs` | **array**                 | Event arguments |

***
