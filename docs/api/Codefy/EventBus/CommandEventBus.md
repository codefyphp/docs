***

# CommandEventBus





* Full name: `\Codefy\EventBus\CommandEventBus`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Codefy\EventBus\EventBus`](./EventBus.md)
* This class is a **Final class**



## Properties


### subscribers



```php
private array $subscribers
```






***

### eventStore



```php
public \Codefy\Domain\EventSourcing\EventStore $eventStore
```






***

### publisher



```php
public \Codefy\EventBus\DomainEventPublisher $publisher
```






***

## Methods


### __construct



```php
public __construct(\Codefy\Domain\EventSourcing\EventStore $eventStore, \Codefy\EventBus\DomainEventPublisher $publisher): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventStore` | **\Codefy\Domain\EventSourcing\EventStore** |  |
| `$publisher` | **\Codefy\EventBus\DomainEventPublisher** |  |





***

### __clone



```php
public __clone(): mixed
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

### unsubscribe



```php
public unsubscribe(\Codefy\EventBus\DomainEventSubscriber $subscriber): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$subscriber` | **\Codefy\EventBus\DomainEventSubscriber** |  |





***

### publish



```php
public publish(\Codefy\Domain\EventSourcing\DomainEvent $events): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$events` | **\Codefy\Domain\EventSourcing\DomainEvent** |  |





***

### getSubscriberUniqueKey



```php
private getSubscriberUniqueKey(\Codefy\EventBus\DomainEventSubscriber $subscriber): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$subscriber` | **\Codefy\EventBus\DomainEventSubscriber** |  |





***


***
> Automatically generated on 2025-10-13
