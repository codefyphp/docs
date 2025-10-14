***

# SimpleProvider





* Full name: `\Qubus\EventDispatcher\Providers\SimpleProvider`
* This class implements:
[`\Psr\EventDispatcher\ListenerProviderInterface`](../../../Psr/EventDispatcher/ListenerProviderInterface.md)



## Properties


### listeners



```php
private array $listeners
```






***

## Methods


### listen



```php
public listen(string $eventClass, callable $listener): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventClass` | **string** |  |
| `$listener` | **callable** |  |





***

### getListenersForEvent



```php
public getListenersForEvent(object $event): iterable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$event` | **object** |  |





***


***
> Automatically generated on 2025-10-13
