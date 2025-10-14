***

# EventBus





* Full name: `\Codefy\EventBus\EventBus`



## Methods


### publish



```php
public publish(\Codefy\Domain\EventSourcing\DomainEvent $events): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$events` | **\Codefy\Domain\EventSourcing\DomainEvent** |  |





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


***
> Automatically generated on 2025-10-13
