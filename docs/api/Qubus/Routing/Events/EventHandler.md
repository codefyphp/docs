# EventHandler

***

* Full name: `\Qubus\Routing\Events\EventHandler`

## Methods

### getEvents

Get events.

```php
public getEvents(string|null $name = null): array
```

**Parameters:**

| Parameter | Type             | Description            |
|-----------|------------------|------------------------|
| `$name`   | **string\|null** | Filter events by name. |

***

### fireEvents

Fires any events registered with given event-name.

```php
public fireEvents(\Qubus\Routing\Router $router, string $name, array $eventArgs = []): void
```

**Parameters:**

| Parameter    | Type                      | Description      |
|--------------|---------------------------|------------------|
| `$router`    | **\Qubus\Routing\Router** | Router instance. |
| `$name`      | **string**                | Event name.      |
| `$eventArgs` | **array**                 | Event arguments. |

***
