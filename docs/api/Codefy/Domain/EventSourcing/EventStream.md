# EventStream

***

* Full name: `\Codefy\Domain\EventSourcing\EventStream`
* Parent class: [`\Codefy\Domain\EventSourcing\DomainEvents`](./DomainEvents.md)

## Properties

### aggregateId

```php
public \Codefy\Domain\Aggregate\AggregateId $aggregateId
```

***

## Methods

### __construct

```php
public __construct(\Codefy\Domain\Aggregate\AggregateId $aggregateId, \Codefy\Domain\EventSourcing\DomainEvent[] $events): mixed
```

**Parameters:**

| Parameter      | Type                                           | Description |
|----------------|------------------------------------------------|-------------|
| `$aggregateId` | **\Codefy\Domain\Aggregate\AggregateId**       |             |
| `$events`      | **\Codefy\Domain\EventSourcing\DomainEvent[]** |             |

**Throws:**

- [`CorruptEventStreamException`](./CorruptEventStreamException.md)

***

### aggregateId

```php
public aggregateId(): \Codefy\Domain\Aggregate\AggregateId
```

***

## Inherited methods

### __construct

```php
protected __construct(\Codefy\Domain\EventSourcing\DomainEvent[] $events): mixed
```

**Parameters:**

| Parameter | Type                                           | Description |
|-----------|------------------------------------------------|-------------|
| `$events` | **\Codefy\Domain\EventSourcing\DomainEvent[]** |             |

***

### count

```php
final public count(): int
```

* This method is **final**.
***

### createEmpty

```php
public static createEmpty(): static
```

* This method is **static**.
***

### fromArray

```php
public static fromArray(\Codefy\Domain\EventSourcing\DomainEvent[] $events): static
```

* This method is **static**.
**Parameters:**

| Parameter | Type                                           | Description |
|-----------|------------------------------------------------|-------------|
| `$events` | **\Codefy\Domain\EventSourcing\DomainEvent[]** |             |

***

### withSingleEvent

```php
public static withSingleEvent(\Codefy\Domain\EventSourcing\DomainEvent $event): static
```

* This method is **static**.
**Parameters:**

| Parameter | Type                                         | Description |
|-----------|----------------------------------------------|-------------|
| `$event`  | **\Codefy\Domain\EventSourcing\DomainEvent** |             |

***

### appendEvent

```php
public appendEvent(\Codefy\Domain\EventSourcing\DomainEvent $event): static
```

**Parameters:**

| Parameter | Type                                         | Description |
|-----------|----------------------------------------------|-------------|
| `$event`  | **\Codefy\Domain\EventSourcing\DomainEvent** |             |

***

### appendEvents

```php
public appendEvents(self $more): static
```

**Parameters:**

| Parameter | Type     | Description |
|-----------|----------|-------------|
| `$more`   | **self** |             |

***

### getIterator

```php
public getIterator(): \ArrayIterator
```

***

### toArray

```php
public toArray(): array
```

**Throws:**

- [`Exception`](../../../Exception.md)

***

### map

```php
public map(callable $callback): static
```

**Parameters:**

| Parameter   | Type         | Description |
|-------------|--------------|-------------|
| `$callback` | **callable** |             |

***

### filter

```php
public filter(callable $callback): static
```

**Parameters:**

| Parameter   | Type         | Description |
|-------------|--------------|-------------|
| `$callback` | **callable** |             |

***

### getFirstEvent

```php
public getFirstEvent(): \Codefy\Domain\EventSourcing\DomainEvent
```

***

### isEmpty

```php
public isEmpty(): bool
```

***
