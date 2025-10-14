***

# AggregateChanged

Something that happened in the past and that is of importance to the business.



* Full name: `\Codefy\Domain\EventSourcing\AggregateChanged`
* This class implements:
[`\Codefy\Domain\EventSourcing\DomainEvent`](./DomainEvent.md)


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`DATE_FORMAT`|public| |&#039;Y-m-d H:i:s.u&#039;|

## Properties


### payload



```php
public ?array $payload
```






***

### metadata



```php
protected ?array $metadata
```






***

### recordedAt



```php
protected ?\DateTimeInterface $recordedAt
```






***

## Methods


### __construct



```php
private __construct(\Codefy\Domain\Aggregate\AggregateId $aggregateId, ?array $payload, ?array $metadata = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$aggregateId` | **\Codefy\Domain\Aggregate\AggregateId** |  |
| `$payload` | **?array** |  |
| `$metadata` | **?array** |  |





***

### occur

Named constructor for generating a domain event.

```php
final public static occur(\Codefy\Domain\Aggregate\AggregateId $aggregateId, array $payload, array $metadata = []): self
```



* This method is **static**.

* This method is **final**.


**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$aggregateId` | **\Codefy\Domain\Aggregate\AggregateId** |  |
| `$payload` | **array** |  |
| `$metadata` | **array** |  |





***

### fromArray

Named constructor for generating a domain event from an array.

```php
final public static fromArray(array $data): \Codefy\Domain\EventSourcing\DomainEvent
```



* This method is **static**.

* This method is **final**.


**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |





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

### aggregateId

The ID of the Aggregate this event belongs to.

```php
public aggregateId(): \Codefy\Domain\Aggregate\AggregateId
```












***

### eventId

Uuid of the event.

```php
public eventId(): string|\Codefy\Domain\EventSourcing\EventId
```












***

### metadata

Event metadata.

```php
public metadata(): array
```












***

### playhead

Aggregate version.

```php
public playhead(): int
```












***

### recordedAt

The date the event occurred on.

```php
public recordedAt(): string|\DateTimeInterface
```












***

### toArray

Returns array of event data.

```php
public toArray(): array
```












***

### param

Retrieve data from payload by name.

```php
public param(string $name, mixed $default = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$default` | **mixed** |  |





***

### metaParam

Retrieve meta data from metadata by name.

```php
public metaParam(string $name, mixed $default = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$default` | **mixed** |  |





***

### withMetadata

Append event metadata.

```php
final public withMetadata(array $metadata): self
```





* This method is **final**.


**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$metadata` | **array** |  |





***

### withAddedMetadata

Append event metadata.

```php
final public withAddedMetadata(string $key, mixed $value): self
```





* This method is **final**.


**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |
| `$value` | **mixed** |  |





***

### withPlayhead

Append event version.

```php
final public withPlayhead(int $playhead): self
```





* This method is **final**.


**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$playhead` | **int** |  |





***

### setEventId



```php
private setEventId(\Codefy\Domain\EventSourcing\EventId $eventId): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventId` | **\Codefy\Domain\EventSourcing\EventId** |  |





***

### setEventType



```php
private setEventType(string $eventType): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$eventType` | **string** |  |





***

### setAggregateId



```php
private setAggregateId(\Codefy\Domain\Aggregate\AggregateId $aggregateId): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$aggregateId` | **\Codefy\Domain\Aggregate\AggregateId** |  |





***

### setPlayhead



```php
private setPlayhead(int $playhead): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$playhead` | **int** |  |





***

### setPayload



```php
private setPayload(?array $payload): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$payload` | **?array** |  |





***

### init



```php
private init(): void
```












***


***
> Automatically generated on 2025-10-13
