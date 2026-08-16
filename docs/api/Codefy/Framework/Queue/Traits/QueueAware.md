# QueueAware

***

* Full name: `\Codefy\Framework\Queue\Traits\QueueAware`

## Properties

### name

The name of the queue this instance is working with.

```php
public string $name
```

***
### leaseTime

How long the processing is expected to take in seconds.

```php
public int $leaseTime
```

***
### schedule

When should the process run.

```php
public string $schedule
```

***
### executions

How many times should a job execute before
considered dead.

```php
public int $executions
```

***
