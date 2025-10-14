***

# GenericEvent





* Full name: `\Qubus\EventDispatcher\Legacy\GenericEvent`
* Parent class: [`\Qubus\EventDispatcher\BaseEvent`](../BaseEvent.md)
* This class implements:
[`\Qubus\EventDispatcher\Legacy\Event`](./Event.md)



## Properties


### name

The event name.

```php
protected string $name
```






***

### subject

The subject.

```php
protected ?object $subject
```






***

### arguments

Array of arguments.

```php
protected array $arguments
```






***

## Methods


### __construct



```php
public __construct(string $name = &#039;&#039;, object|null $subject = null, array $arguments = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$subject` | **object&#124;null** |  |
| `$arguments` | **array** |  |





***

### getName

Gets the event name.

```php
public getName(): string
```












***

### setName

Sets the event name.

```php
public setName(string $name): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### setSubject

Sets the subject.

```php
public setSubject(object|null $subject): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$subject` | **object&#124;null** |  |





***

### getSubject

Gets the subject.

```php
public getSubject(): null|object
```












***

### setArgument

Sets a argument to the event.

```php
public setArgument(string $name, mixed $value): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$value` | **mixed** |  |





***

### getArgument

Gets the argument by its key.

```php
public getArgument(string $name): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### setArguments

Sets array of arguments.

```php
public setArguments(array $arguments): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$arguments` | **array** |  |





***

### getArguments

Gets all arguments.

```php
public getArguments(): array
```












***

### hasArgument

Has argument.

```php
public hasArgument(string $key): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |





***


## Inherited methods


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
