***

# AggregateRepository





* Full name: `\Codefy\Domain\Aggregate\AggregateRepository`



## Methods


### loadAggregateRoot

Loads an aggregate from the given aggregate id.

```php
public loadAggregateRoot(\Codefy\Domain\Aggregate\AggregateId $aggregateId): \Codefy\Domain\Aggregate\RecordsEvents|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$aggregateId` | **\Codefy\Domain\Aggregate\AggregateId** |  |




**Throws:**

- [`AggregateNotFoundException`](./AggregateNotFoundException.md)



***

### saveAggregateRoot

Persist an aggregate.

```php
public saveAggregateRoot(\Codefy\Domain\Aggregate\RecordsEvents $aggregate): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$aggregate` | **\Codefy\Domain\Aggregate\RecordsEvents** |  |





***


***
> Automatically generated on 2025-10-13
