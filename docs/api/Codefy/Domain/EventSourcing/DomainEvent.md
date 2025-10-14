***

# DomainEvent

Something that happened in the past and that is of importance to the business.



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
public recordedAt(): string|\DateTimeInterface
```












***

### withPlayhead

Append event version.

```php
public withPlayhead(int $playhead): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$playhead` | **int** |  |





***

### playhead

Version of the recorded event.

```php
public playhead(): int
```












***


***
> Automatically generated on 2025-10-13
