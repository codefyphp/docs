***

# UnitOfWork

A unit of work that acts both as an identity map and a change tracker.

It does not commit/save/persist. Its role is reduced to tracking multiple
aggregates, and to hand you back those that have changed. Persisting the
ones that have changed or happened on the outside.

* Full name: `\Codefy\Domain\UnitOfWork`
* Parent interfaces: [`\Codefy\Domain\IdentityMap`](./IdentityMap.md)


## Methods


### getChanges

Returns AggregateRoots that have changed.

```php
public getChanges(): \Codefy\Domain\Aggregate\RecordsEvents[]
```












***


## Inherited methods


### attachToIdentityMap

Attach an aggregate to the map.

```php
public attachToIdentityMap(\Codefy\Domain\Aggregate\RecordsEvents $aggregate): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$aggregate` | **\Codefy\Domain\Aggregate\RecordsEvents** |  |





***

### retrieveFromIdentityMap

Retrieve an aggregate from the map by its aggregate id.

```php
public retrieveFromIdentityMap(\Codefy\Domain\Aggregate\AggregateId $aggregateId): \Codefy\Domain\Aggregate\RecordsEvents|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$aggregateId` | **\Codefy\Domain\Aggregate\AggregateId** |  |





***


***
> Automatically generated on 2025-10-13
