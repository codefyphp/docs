***

# EventName





* Full name: `\Codefy\Domain\EventSourcing\EventName`



## Properties


### name



```php
protected ?\Qubus\ValueObjects\StringLiteral\StringLiteral $name
```






***

### event



```php
public \Codefy\Domain\EventSourcing\DomainEvent $event
```






***

## Methods


### __construct



```php
public __construct(\Codefy\Domain\EventSourcing\DomainEvent $event): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$event` | **\Codefy\Domain\EventSourcing\DomainEvent** |  |





***

### __toString



```php
public __toString(): string
```











**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### parseName



```php
private parseName(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```











**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***


***
> Automatically generated on 2025-10-13
