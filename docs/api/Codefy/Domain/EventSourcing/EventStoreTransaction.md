***

# EventStoreTransaction

Code originated at https://github.com/beberlei/litecqrs-php/



* Full name: `\Codefy\Domain\EventSourcing\EventStoreTransaction`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Codefy\Domain\EventSourcing\Transactional`](./Transactional.md)
* This class is a **Final class**



## Properties


### transactionId



```php
public \Codefy\Domain\EventSourcing\TransactionId $transactionId
```






***

### eventStream



```php
public \Codefy\Domain\EventSourcing\DomainEvents $eventStream
```






***

### committedEvents



```php
public array $committedEvents
```






***

## Methods


### __construct



```php
public __construct(\Codefy\Domain\EventSourcing\TransactionId $transactionId, \Codefy\Domain\EventSourcing\DomainEvents $eventStream, array $committedEvents): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$transactionId` | **\Codefy\Domain\EventSourcing\TransactionId** |  |
| `$eventStream` | **\Codefy\Domain\EventSourcing\DomainEvents** |  |
| `$committedEvents` | **array** |  |





***


***
> Automatically generated on 2025-10-13
