***

# ListenerPriorityQueue





* Full name: `\Qubus\EventDispatcher\Legacy\ListenerPriorityQueue`
* This class implements:
[`\IteratorAggregate`](../../../IteratorAggregate.md)



## Properties


### storage



```php
protected \SplObjectStorage $storage
```






***

### queue



```php
protected \SplPriorityQueue $queue
```






***

## Methods


### __construct



```php
public __construct(\SplObjectStorage $storage = new SplObjectStorage(), \SplPriorityQueue $queue = new SplPriorityQueue()): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$storage` | **\SplObjectStorage** |  |
| `$queue` | **\SplPriorityQueue** |  |





***

### insert

Insert a listener to the queue.

```php
public insert(\Qubus\EventDispatcher\Legacy\EventListener $listener, int $priority): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$listener` | **\Qubus\EventDispatcher\Legacy\EventListener** |  |
| `$priority` | **int** |  |





***

### detach

Removes an listener from the queue.

```php
public detach(\Qubus\EventDispatcher\Legacy\EventListener $listener): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$listener` | **\Qubus\EventDispatcher\Legacy\EventListener** |  |





***

### clear

Clears the queue.

```php
public clear(): void
```












***

### contains

Checks whether the queue contains the listener.

```php
public contains(\Qubus\EventDispatcher\Legacy\EventListener $listener): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$listener` | **\Qubus\EventDispatcher\Legacy\EventListener** |  |





***

### all

Gets all listeners.

```php
public all(): \Qubus\EventDispatcher\Legacy\EventListener[]
```












***

### getIterator

Clones and returns a iterator.

```php
public getIterator(): \Traversable
```












***

### refreshQueue

Refreshes the status of the queue.

```php
protected refreshQueue(): void
```












***


***
> Automatically generated on 2025-10-13
