# IsEventSourced

***

* Full name: `\Codefy\Domain\Aggregate\IsEventSourced`

## Methods

### reconstituteFromEventStream

Reconstitutes an Aggregate instance from its history of domain events.

```php
public static reconstituteFromEventStream(\Codefy\Domain\EventSourcing\EventStream $aggregateHistory): \Codefy\Domain\Aggregate\RecordsEvents
```

* This method is **static**.
**Parameters:**

| Parameter           | Type                                         | Description |
|---------------------|----------------------------------------------|-------------|
| `$aggregateHistory` | **\Codefy\Domain\EventSourcing\EventStream** |             |

***
