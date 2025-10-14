***

# DomainEventsArray





* Full name: `\Codefy\Domain\EventSourcing\DomainEventsArray`
* This class implements:
[`\Countable`](../../../Countable.md), [`\IteratorAggregate`](../../../IteratorAggregate.md)
* This class is an **Abstract class**



## Properties


### events



```php
private array $events
```






***

### iterator



```php
private \ArrayIterator $iterator
```






***

## Methods


### __construct



```php
protected __construct(array $events): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$events` | **array** |  |





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
public static fromArray(array $events): static
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$events` | **array** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### withSingleEvent



```php
public static withSingleEvent(\Codefy\Domain\EventSourcing\DomainEvent $event): static
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$event` | **\Codefy\Domain\EventSourcing\DomainEvent** |  |





***

### appendEvent



```php
public appendEvent(\Codefy\Domain\EventSourcing\DomainEvent $event): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$event` | **\Codefy\Domain\EventSourcing\DomainEvent** |  |





***

### appendEvents



```php
public appendEvents(self $more): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$more` | **self** |  |





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

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **callable** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### filter



```php
public filter(callable $callback): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **callable** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



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


***
> Automatically generated on 2025-10-13
