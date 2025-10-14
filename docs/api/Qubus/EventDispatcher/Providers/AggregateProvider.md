***

# AggregateProvider

AggregateProvider is a listener provider that allows combining multiple listener providers.



* Full name: `\Qubus\EventDispatcher\Providers\AggregateProvider`
* This class implements:
[`\Psr\EventDispatcher\ListenerProviderInterface`](../../../Psr/EventDispatcher/ListenerProviderInterface.md)



## Properties


### providers



```php
private \Psr\EventDispatcher\ListenerProviderInterface[] $providers
```






***

## Methods


### __construct



```php
public __construct(\Psr\EventDispatcher\ListenerProviderInterface $providers): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$providers` | **\Psr\EventDispatcher\ListenerProviderInterface** |  |





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

### attach



```php
public attach(\Psr\EventDispatcher\ListenerProviderInterface $provider): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$provider` | **\Psr\EventDispatcher\ListenerProviderInterface** |  |





***


***
> Automatically generated on 2025-10-13
