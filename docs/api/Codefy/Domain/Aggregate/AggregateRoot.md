# AggregateRoot

Entities that are an aggregate root.

***

* Full name: `\Codefy\Domain\Aggregate\AggregateRoot`
* Parent interfaces:
  [`\Codefy\Domain\Aggregate\RecordsEvents`](./RecordsEvents.md),
  [`\Codefy\Domain\Model\Entity`](../Model/Entity.md)

## Inherited methods

### aggregateId

Returns unique aggregate id.

```php
public aggregateId(): \Codefy\Domain\Aggregate\AggregateId
```

***

### hasRecordedEvents

Determine whether the object's state has changed since the last clearRecordedEvent();

```php
public hasRecordedEvents(): bool
```

***

### getRecordedEvents

Get all the Domain Events that were recorded since the last time it was cleared, or since it was
restored from persistence. This does not include events that were recorded prior.

```php
public getRecordedEvents(): \Codefy\Domain\EventSourcing\DomainEvents
```

***

### clearRecordedEvents

Clears the record of new Domain Events. This doesn't clear the history of the object.

```php
public clearRecordedEvents(): void
```

***
