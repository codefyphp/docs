***

# Queue

Interface for a queue.

Classes implementing this interface will do a best effort to preserve order
in messages and to execute them at least once.

* Full name: `\Codefy\Framework\Queue\Queue`



## Methods


### createItem

Adds a queue item and store it directly to the queue.

```php
public createItem(): string
```









**Return Value:**

A unique ID if the item was successfully created and was (best effort)
added to the queue, otherwise FALSE. We don't guarantee the item was
committed to disk etc, but as far as we know, the item is now in the
queue.




***

### numberOfItems

Retrieves the number of items in the queue.

```php
public numberOfItems(): int
```

This is intended to provide a "best guess" count of the number of items in
the queue. Depending on the implementation and the setup, the accuracy of
the results of this function may vary.

e.g. On a busy system with a large number of consumers and items, the
result might only be valid for a fraction of a second and not provide an
accurate representation.







**Return Value:**

An integer estimate of the number of items in the queue.




***

### claimItem

Claims an item in the queue for processing.

```php
public claimItem(int $leaseTime = 3600): array|object|bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$leaseTime` | **int** | How long the processing is expected to take in seconds,<br />defaults to an hour. After this lease expires, the item<br />will be reset and another consumer can claim the item.<br />For idempotent tasks (which can be run multiple times<br />without side effects), shorter lease times would result<br />in lower latency in case a consumer fails. For tasks<br />that should not be run more than once (non-idempotent),<br />a larger lease time will make it more rare for a given<br />task to run multiple times in cases of failure, at the<br />cost of higher latency. |


**Return Value:**

On success, we return an item object|array. If the queue is
                  unable to claim an item it returns false. This implies
                  a best effort to retrieve an item and either the queue
                  is empty or there is some other non-recoverable problem.

If returned, the object|array will have at least the following properties:
- data: the same as what was passed into createItem().
- _id: the unique ID returned from createItem().
- created: timestamp when the item was put into the queue.




***

### deleteItem

Deletes a finished item from the queue.

```php
public deleteItem(mixed $item): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$item` | **mixed** | The item returned by claimItem(). |





***

### releaseItem

Releases an item that the worker could not process.

```php
public releaseItem(mixed $item): bool
```

Another worker can come in and process it before the timeout expires.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$item` | **mixed** | The item returned by claimItem(). |


**Return Value:**

TRUE if the item has been released, FALSE otherwise.




***

### createQueue

Creates a queue.

```php
public createQueue(): mixed
```

Called during installation and should be used to perform any necessary
initialization operations. This should not be confused with the
constructor for these objects, which is called every time an object is
instantiated to operate on a queue. This operation is only needed the
first time a given queue is going to be initialized (for example, to make
a new database table or directory to hold tasks for the queue -- it
depends on the queue implementation if this is necessary at all).










***

### deleteQueue

Deletes a queue and every item in the queue.

```php
public deleteQueue(): void
```












***


***
> Automatically generated on 2025-10-13
