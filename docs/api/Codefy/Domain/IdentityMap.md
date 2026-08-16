# IdentityMap

Holds unique Aggregate instances in memory, mapped by id.

Useful to make sure an Aggregate is not loaded twice.

***

* Full name: `\Codefy\Domain\IdentityMap`

## Methods

### attachToIdentityMap

Attach an aggregate to the map.

```php
public attachToIdentityMap(\Codefy\Domain\Aggregate\RecordsEvents $aggregate): void
```

**Parameters:**

| Parameter    | Type                                       | Description |
|--------------|--------------------------------------------|-------------|
| `$aggregate` | **\Codefy\Domain\Aggregate\RecordsEvents** |             |

***

### retrieveFromIdentityMap

Retrieve an aggregate from the map by its aggregate id.

```php
public retrieveFromIdentityMap(\Codefy\Domain\Aggregate\AggregateId $aggregateId): \Codefy\Domain\Aggregate\RecordsEvents|null
```

**Parameters:**

| Parameter      | Type                                     | Description |
|----------------|------------------------------------------|-------------|
| `$aggregateId` | **\Codefy\Domain\Aggregate\AggregateId** |             |

***
