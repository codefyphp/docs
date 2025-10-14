***

# EventSourcedAggregateRepository





* Full name: `\Codefy\Domain\Aggregate\EventSourcedAggregateRepository`
* This class implements:
[`\Codefy\Domain\Aggregate\AggregateRepository`](./AggregateRepository.md)



## Properties


### eventStore



```php
protected \Codefy\Domain\EventSourcing\EventStore $eventStore
```






***

### projection



```php
protected \Codefy\Domain\EventSourcing\Projection $projection
```






***

## Methods


### __construct



```php
public __construct(\Codefy\Domain\EventSourcing\EventStore $eventStore, \Codefy\Domain\EventSourcing\Projection $projection): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventStore` | **\Codefy\Domain\EventSourcing\EventStore** |  |
| `$projection` | **\Codefy\Domain\EventSourcing\Projection** |  |





***

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

- [`CorruptEventStreamException`](../EventSourcing/CorruptEventStreamException.md)



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

### clearIdentityMap

Clear the identity map.

```php
public clearIdentityMap(): void
```












***

### removeFromIdentityMap

Remove aggregate from identity map.

```php
public removeFromIdentityMap(\Codefy\Domain\Aggregate\RecordsEvents $aggregate): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$aggregate` | **\Codefy\Domain\Aggregate\RecordsEvents** |  |





***

### enableIdentityMap

Set whether identity map is enabled.

```php
public enableIdentityMap(bool $bool = true): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$bool` | **bool** |  |





***


***
> Automatically generated on 2025-10-13
