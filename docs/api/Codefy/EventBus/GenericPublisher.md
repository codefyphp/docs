***

# GenericPublisher





* Full name: `\Codefy\EventBus\GenericPublisher`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Codefy\EventBus\DomainEventPublisher`](./DomainEventPublisher.md)
* This class is a **Final class**



## Properties


### subscribers



```php
protected array $subscribers
```






***

### instance



```php
protected static \Codefy\EventBus\DomainEventPublisher|null $instance
```



* This property is **static**.


***

## Methods


### instance



```php
public static instance(): \Codefy\EventBus\DomainEventPublisher
```



* This method is **static**.








***

### __construct



```php
private __construct(): mixed
```












***

### subscribe



```php
public subscribe(\Codefy\EventBus\DomainEventSubscriber $subscriber): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$subscriber` | **\Codefy\EventBus\DomainEventSubscriber** |  |





***

### publish

Publishes a domain event.

```php
public publish(\Codefy\Domain\EventSourcing\DomainEvent $event): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$event` | **\Codefy\Domain\EventSourcing\DomainEvent** |  |





***


***
> Automatically generated on 2025-10-13
