***

# EventProducerAware





* Full name: `\Codefy\Traits\EventProducerAware`



## Properties


### playhead



```php
protected int $playhead
```






***

### recordedEvents



```php
protected array $recordedEvents
```






***

## Methods


### recordThat

Records domain events.

```php
protected recordThat(\Codefy\Domain\EventSourcing\DomainEvent $event): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$event` | **\Codefy\Domain\EventSourcing\DomainEvent** |  |





***

### pullDomainEvents



```php
public pullDomainEvents(): array
```












***

### when



```php
protected when(\Codefy\Domain\EventSourcing\DomainEvent $event): void
```




* This method is **abstract**.



**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$event` | **\Codefy\Domain\EventSourcing\DomainEvent** |  |





***

***
> Automatically generated on 2025-10-13

