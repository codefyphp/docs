***

# IdentityMapAware





* Full name: `\Codefy\Traits\IdentityMapAware`



## Properties


### identityMap



```php
protected array $identityMap
```






***

### enableIdentityMap



```php
protected bool $enableIdentityMap
```






***

## Methods


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

