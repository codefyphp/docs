# EventStore

Event store for publishing a domain event
and retrieving an aggregate's history.

***

* Full name: `\Codefy\Domain\EventSourcing\EventStore`

## Methods

### append

Append a domain event to the event store.

```php
public append(\Codefy\Domain\EventSourcing\DomainEvent $event): void
```

**Parameters:**

| Parameter | Type                                         | Description |
|-----------|----------------------------------------------|-------------|
| `$event`  | **\Codefy\Domain\EventSourcing\DomainEvent** |             |

***

### commit

Appends a list of domain events to the event store.

```php
public commit(\Codefy\Domain\EventSourcing\DomainEvent $events): \Codefy\Domain\EventSourcing\Transactional
```

**Parameters:**

| Parameter | Type                                         | Description |
|-----------|----------------------------------------------|-------------|
| `$events` | **\Codefy\Domain\EventSourcing\DomainEvent** |             |

***

### getAggregateHistoryFor

Retrieve aggregate's history based on aggregate id.

```php
public getAggregateHistoryFor(\Codefy\Domain\Aggregate\AggregateId $aggregateId): \Codefy\Domain\EventSourcing\EventStream
```

**Parameters:**

| Parameter      | Type                                     | Description |
|----------------|------------------------------------------|-------------|
| `$aggregateId` | **\Codefy\Domain\Aggregate\AggregateId** |             |

**Throws:**

- [`\Codefy\Domain\Aggregate\AggregateNotFoundException|\Codefy\Domain\EventSourcing\CorruptEventStreamException`](../Aggregate/AggregateNotFoundException|/Codefy/Domain/EventSourcing/CorruptEventStreamException.md)

***

### loadFromPlayhead

```php
public loadFromPlayhead(\Codefy\Domain\Aggregate\AggregateId $aggregateId, int $playhead): \Codefy\Domain\EventSourcing\EventStream
```

**Parameters:**

| Parameter      | Type                                     | Description |
|----------------|------------------------------------------|-------------|
| `$aggregateId` | **\Codefy\Domain\Aggregate\AggregateId** |             |
| `$playhead`    | **int**                                  |             |

**Throws:**

- [`\Codefy\Domain\Aggregate\AggregateNotFoundException|\Codefy\Domain\EventSourcing\CorruptEventStreamException`](../Aggregate/AggregateNotFoundException|/Codefy/Domain/EventSourcing/CorruptEventStreamException.md)

***
