# EventSourcedAggregate

***

* Full name: `\Codefy\Domain\Aggregate\EventSourcedAggregate`
* This class implements:
  [`\Codefy\Domain\Aggregate\AggregateRoot`](./AggregateRoot.md),
  [`\Codefy\Domain\Aggregate\IsEventSourced`](./IsEventSourced.md)

## Properties

### aggregateId

```php
public \Codefy\Domain\Aggregate\AggregateId $aggregateId
```

***

## Methods

### __construct

```php
final private __construct(\Codefy\Domain\Aggregate\AggregateId $aggregateId): mixed
```

* This method is **final**.
**Parameters:**

| Parameter      | Type                                     | Description |
|----------------|------------------------------------------|-------------|
| `$aggregateId` | **\Codefy\Domain\Aggregate\AggregateId** |             |

***

### root

```php
final public static root(\Codefy\Domain\Aggregate\AggregateId $aggregateId): static
```

* This method is **static**.* This method is **final**.
**Parameters:**

| Parameter      | Type                                     | Description |
|----------------|------------------------------------------|-------------|
| `$aggregateId` | **\Codefy\Domain\Aggregate\AggregateId** |             |

***

### recordApplyAndPublishThat

Records, applies, and publishes a domain event.

```php
protected recordApplyAndPublishThat(\Codefy\Domain\EventSourcing\DomainEvent $event): void
```

**Parameters:**

| Parameter | Type                                         | Description |
|-----------|----------------------------------------------|-------------|
| `$event`  | **\Codefy\Domain\EventSourcing\DomainEvent** |             |

***

### applyThat

```php
protected applyThat(\Codefy\Domain\EventSourcing\DomainEvent $event): void
```

**Parameters:**

| Parameter | Type                                         | Description |
|-----------|----------------------------------------------|-------------|
| `$event`  | **\Codefy\Domain\EventSourcing\DomainEvent** |             |

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

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

***

### clearRecordedEvents

Clears the record of new Domain Events. This doesn't clear the history of the object.

```php
public clearRecordedEvents(): void
```

***

### aggregateId

Returns unique aggregate id.

```php
public aggregateId(): \Codefy\Domain\Aggregate\AggregateId
```

***

### playhead

Aggregate root version.

```php
public playhead(): int
```

***

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

### equals

```php
final public equals(\Codefy\Domain\Aggregate\AggregateRoot $aggregateRoot): bool
```

* This method is **final**.
**Parameters:**

| Parameter        | Type                                       | Description |
|------------------|--------------------------------------------|-------------|
| `$aggregateRoot` | **\Codefy\Domain\Aggregate\AggregateRoot** |             |

***

### className

Retrieves the class name.

```php
final public static className(): string
```

* This method is **static**.* This method is **final**.
***

## Inherited methods

### publishThat

```php
protected publishThat(\Codefy\Domain\EventSourcing\DomainEvent $event): void
```

**Parameters:**

| Parameter | Type                                         | Description |
|-----------|----------------------------------------------|-------------|
| `$event`  | **\Codefy\Domain\EventSourcing\DomainEvent** |             |

***

### aggregateId

```php
public aggregateId(): \Codefy\Domain\Aggregate\AggregateId
```

* This method is **abstract**.
***

### recordThat

Records domain events.

```php
protected recordThat(\Codefy\Domain\EventSourcing\DomainEvent $event): void
```

**Parameters:**

| Parameter | Type                                         | Description |
|-----------|----------------------------------------------|-------------|
| `$event`  | **\Codefy\Domain\EventSourcing\DomainEvent** |             |

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

| Parameter | Type                                         | Description |
|-----------|----------------------------------------------|-------------|
| `$event`  | **\Codefy\Domain\EventSourcing\DomainEvent** |             |

***
