***

# Action





* Full name: `\Qubus\EventDispatcher\ActionFilter\Action`
* Parent class: [`\Qubus\EventDispatcher\ActionFilter\BaseHooks`](./BaseHooks.md)
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Qubus\EventDispatcher\ActionFilter\Actionable`](./Actionable.md), [`\Qubus\EventDispatcher\ActionFilter\RemoveAllActions`](./RemoveAllActions.md)
* This class is a **Final class**




## Methods


### addAction

Adds an action.

```php
public addAction(string $hook, mixed $callback, int $priority = self::PRIORITY_NEUTRAL, int $arguments = self::ARGUMENT_NEUTRAL): \Qubus\EventDispatcher\ActionFilter\BaseHooks
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$hook` | **string** | Hook name. |
| `$callback` | **mixed** | Function to execute. |
| `$priority` | **int** | Priority of the action. |
| `$arguments` | **int** | Number of arguments to accept. |





***

### doAction

Runs an action.

```php
public doAction(mixed $args): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$args` | **mixed** | First argument will be the name of the hook, and the rest will be args for the hook. |




**Throws:**

- [`Exception`](../../Exception/Exception.md)



***

### removeAction

Removes an action.

```php
public removeAction(string $hook, mixed $callback, int $priority = self::PRIORITY_NEUTRAL): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$hook` | **string** | Hook name. |
| `$callback` | **mixed** | Function to execute. |
| `$priority` | **int** | Priority of the action. |





***

### removeAllActions

Removes all actions.

```php
public removeAllActions(?string $hook = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$hook` | **?string** | Hook name. |





***

### trigger

Runs an action.

```php
protected trigger(string $action, array $args): void
```

When an action is triggered, all hooks are run in the order supplied when adding them.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$action` | **string** | Name of action. |
| `$args` | **array** | Arguments passed to the filter. |




**Throws:**

- [`Exception`](../../Exception/Exception.md)



***


## Inherited methods


### listen

Adds a hook.

```php
public listen(string $hook, mixed $callback, int $priority = self::PRIORITY_NEUTRAL, int $arguments = self::ARGUMENT_NEUTRAL): \Qubus\EventDispatcher\ActionFilter\BaseHooks
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$hook` | **string** | Hook name. |
| `$callback` | **mixed** | Function to execute. |
| `$priority` | **int** | Priority of the action. |
| `$arguments` | **int** | Number of arguments to accept. |





***

### remove

Removes a hook.

```php
public remove(string $hook, mixed $callback, int $priority = self::PRIORITY_NEUTRAL): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$hook` | **string** | Hook name. |
| `$callback` | **mixed** | Function to execute. |
| `$priority` | **int** | Priority of the action. |





***

### removeAll

Remove all hooks with given hook in collection. If no hook, clear all hooks.

```php
public removeAll(string|null $hook = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$hook` | **string&#124;null** | Hook name. |





***

### getHooks

Gets a sorted list of all hooks.

```php
public getHooks(): array
```












***

### getFunction

Gets the function.

```php
protected getFunction(mixed $callback): callable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **mixed** | Callback. |


**Return Value:**

A closure



**Throws:**

- [`Exception`](../../Exception/Exception.md)



***

### createHook

Figures out the hook.

```php
protected createHook(mixed $args): \stdClass
```

Will return an object with two keys. One for the name and one for the arguments that will be
passed to the hook itself.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$args` | **mixed** |  |





***

### trigger

Fires a new action/filter.

```php
protected trigger(string $action, mixed $args): mixed
```




* This method is **abstract**.



**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$action` | **string** | Name of action |
| `$args` | **mixed** | Arguments passed to the action |





***


***
> Automatically generated on 2025-10-13
