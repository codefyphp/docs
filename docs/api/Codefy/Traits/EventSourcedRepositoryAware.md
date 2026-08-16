# EventSourcedRepositoryAware

***

* Full name: `\Codefy\Traits\EventSourcedRepositoryAware`

## Methods

### loadAggregateRoot

{@inheritDoc}

```php
public loadAggregateRoot(\Codefy\Domain\Aggregate\AggregateId $aggregateId): \Codefy\Domain\Aggregate\RecordsEvents
```

**Parameters:**

| Parameter      | Type                                     | Description |
|----------------|------------------------------------------|-------------|
| `$aggregateId` | **\Codefy\Domain\Aggregate\AggregateId** |             |

**Throws:**

- [`CorruptEventStreamException`](../Domain/EventSourcing/CorruptEventStreamException.md)

***
### saveAggregateRoot

{@inheritDoc}

```php
public saveAggregateRoot(\Codefy\Domain\Aggregate\RecordsEvents $aggregate): void
```

**Parameters:**

| Parameter    | Type                                       | Description |
|--------------|--------------------------------------------|-------------|
| `$aggregate` | **\Codefy\Domain\Aggregate\RecordsEvents** |             |

***
