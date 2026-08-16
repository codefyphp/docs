# DbTransactionsAware

***

* Full name: `\Codefy\Framework\Support\Traits\DbTransactionsAware`

## Properties

### useTransaction

Determines whether class uses transaction.

```php
protected bool $useTransaction
```

***

## Methods

### withTransaction

Enable transaction in pipeline.

```php
public withTransaction(): static
```

***
### beginTransaction

Begin the transaction if enabled.

```php
protected beginTransaction(): void
```

***
### commitTransaction

Commit the transaction if enabled.

```php
protected commitTransaction(): void
```

***
### rollbackTransaction

Rollback the transaction if enabled.

```php
protected rollbackTransaction(): void
```

***
