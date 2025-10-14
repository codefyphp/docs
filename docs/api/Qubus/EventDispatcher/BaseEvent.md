***

# BaseEvent





* Full name: `\Qubus\EventDispatcher\BaseEvent`
* This class implements:
[`\Psr\EventDispatcher\StoppableEventInterface`](../../Psr/EventDispatcher/StoppableEventInterface.md)
* This class is an **Abstract class**



## Properties


### propagationStopped



```php
protected bool $propagationStopped
```






***

## Methods


### isPropagationStopped

{@inheritdoc}

```php
public isPropagationStopped(): bool
```












***

### stopPropagation

Stops the propagation of the event to further event listeners.

```php
public stopPropagation(): void
```












***


***
> Automatically generated on 2025-10-13
