# DomainEvent

Something that happened in the past and that is of importance to the business.

***

* Full name: `\Codefy\Domain\EventSourcing\DomainEvent`

## Methods

### aggregateId

The ID of the Aggregate this event belongs to.

```php
public aggregateId(): \Codefy\Domain\Aggregate\AggregateId
```

***

### recordedAt

Date the event was recorded on.

```php
public recordedAt(): ?\DateTimeInterface
```

***

### withPlayhead

Append event version.

```php
public withPlayhead(int $playhead): self
```

**Parameters:**

| Parameter   | Type    | Description |
|-------------|---------|-------------|
| `$playhead` | **int** |             |

***

### playhead

Version of the recorded event.

```php
public playhead(): int
```

***

### payload

Returns payload array.

```php
public payload(): array
```

***

### eventType

Name of the event.

```php
public eventType(): string
```

***

### eventId

Uuid of the event.

```php
public eventId(): \Codefy\Domain\EventSourcing\EventId
```

***

### metadata

Event metadata.

```php
public metadata(): array
```

***

### metaParam

Retrieve meta data from metadata by name.

```php
public metaParam(string $name, mixed $default = null): mixed
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$name`    | **string** |             |
| `$default` | **mixed**  |             |

***
