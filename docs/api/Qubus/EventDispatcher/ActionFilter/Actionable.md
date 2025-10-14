***

# Actionable





* Full name: `\Qubus\EventDispatcher\ActionFilter\Actionable`



## Methods


### addAction

Adds an action.

```php
public addAction(string $hook, mixed $callback, int $priority = 10, int $arguments = 1): \Qubus\EventDispatcher\ActionFilter\BaseHooks
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

Actions never return anything. It is merely a way of executing code at a specific time in your code.
You can add as many parameters as you'd like.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$args` | **mixed** | First argument will be the name of the hook, and the rest will be args for the hook. |





***

### removeAction

Removes an action.

```php
public removeAction(string $hook, mixed $callback, int $priority = 10): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$hook` | **string** | Hook name. |
| `$callback` | **mixed** | Function to execute. |
| `$priority` | **int** | Priority of the action. |





***


***
> Automatically generated on 2025-10-13
