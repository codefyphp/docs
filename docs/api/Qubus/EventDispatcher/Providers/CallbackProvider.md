***

# CallbackProvider





* Full name: `\Qubus\EventDispatcher\Providers\CallbackProvider`
* This class implements:
[`\Psr\EventDispatcher\ListenerProviderInterface`](../../../Psr/EventDispatcher/ListenerProviderInterface.md)



## Properties


### callbacks



```php
protected array&lt;string,string[]&gt; $callbacks
```






***

## Methods


### getListenersForEvent



```php
public getListenersForEvent(object $event): iterable&lt;callable&gt;
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$event` | **object** |  |





***

### addCallbackMethod



```php
public addCallbackMethod(string $type, string $method): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$type` | **string** |  |
| `$method` | **string** |  |





***


***
> Automatically generated on 2025-10-13
