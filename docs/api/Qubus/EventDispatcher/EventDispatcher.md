***

# EventDispatcher





* Full name: `\Qubus\EventDispatcher\EventDispatcher`
* This class implements:
[`\Psr\EventDispatcher\EventDispatcherInterface`](../../Psr/EventDispatcher/EventDispatcherInterface.md)



## Properties


### listenerProvider



```php
private ?\Psr\EventDispatcher\ListenerProviderInterface $listenerProvider
```






***

## Methods


### __construct



```php
public __construct(\Psr\EventDispatcher\ListenerProviderInterface $listenerProvider): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$listenerProvider` | **\Psr\EventDispatcher\ListenerProviderInterface** |  |





***

### dispatch

{@inheritDoc}

```php
public dispatch(object $event): object
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$event` | **object** |  |





***


***
> Automatically generated on 2025-10-13
