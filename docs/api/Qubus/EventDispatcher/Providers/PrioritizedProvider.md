***

# PrioritizedProvider





* Full name: `\Qubus\EventDispatcher\Providers\PrioritizedProvider`
* This class implements:
[`\Psr\EventDispatcher\ListenerProviderInterface`](../../../Psr/EventDispatcher/ListenerProviderInterface.md)



## Properties


### listeners



```php
private array $listeners
```






***

## Methods


### getListenersForEvent



```php
public getListenersForEvent(object $event): iterable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$event` | **object** |  |





***

### listen



```php
public listen(string $eventType, callable $listener, int $priority = 1): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventType` | **string** |  |
| `$listener` | **callable** |  |
| `$priority` | **int** |  |





***


***
> Automatically generated on 2025-10-13
