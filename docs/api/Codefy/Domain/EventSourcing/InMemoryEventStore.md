***

# InMemoryEventStore





* Full name: `\Codefy\Domain\EventSourcing\InMemoryEventStore`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Codefy\Domain\EventSourcing\EventStore`](./EventStore.md)
* This class is a **Final class**



## Properties


### events



```php
private array $events
```






***

## Methods


### append

Append a domain event to the event store.

```php
public append(\Codefy\Domain\EventSourcing\DomainEvent $event): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$event` | **\Codefy\Domain\EventSourcing\DomainEvent** |  |





***

### commit

Appends a list of domain events to the event store.

```php
public commit(\Codefy\Domain\EventSourcing\DomainEvent $events): \Codefy\Domain\EventSourcing\Transactional
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$events` | **\Codefy\Domain\EventSourcing\DomainEvent** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### getAggregateHistoryFor

Retrieve aggregate's history based on aggregate id.

```php
public getAggregateHistoryFor(\Codefy\Domain\Aggregate\AggregateId $aggregateId): \Codefy\Domain\EventSourcing\EventStream
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$aggregateId` | **\Codefy\Domain\Aggregate\AggregateId** |  |




**Throws:**

- [`\Codefy\Domain\EventSourcing\CorruptEventStreamException|\Codefy\Domain\EventSourcing\EventStreamIsEmptyException`](./CorruptEventStreamException|/Codefy/Domain/EventSourcing/EventStreamIsEmptyException.md)



***

### loadFromPlayhead



```php
public loadFromPlayhead(\Codefy\Domain\Aggregate\AggregateId $aggregateId, int $playhead): \Codefy\Domain\EventSourcing\EventStream
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$aggregateId` | **\Codefy\Domain\Aggregate\AggregateId** |  |
| `$playhead` | **int** |  |




**Throws:**

- [`\Codefy\Domain\EventSourcing\CorruptEventStreamException|\Codefy\Domain\EventSourcing\EventStreamIsEmptyException`](./CorruptEventStreamException|/Codefy/Domain/EventSourcing/EventStreamIsEmptyException.md)



***


***
> Automatically generated on 2025-10-13
