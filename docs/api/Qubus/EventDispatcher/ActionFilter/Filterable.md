***

# Filterable





* Full name: `\Qubus\EventDispatcher\ActionFilter\Filterable`



## Methods


### addFilter

Adds a filter.

```php
public addFilter(string $hook, mixed $callback, int $priority = 10, int $arguments = 1): \Qubus\EventDispatcher\ActionFilter\BaseHooks
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$hook` | **string** | Hook name. |
| `$callback` | **mixed** | Function to execute. |
| `$priority` | **int** | Priority of the filter. |
| `$arguments` | **int** | Number of arguments to accept. |





***

### applyFilter

Runs a filter.

```php
public applyFilter(array $args): mixed
```

Filters should always return something. The first parameter will always be the default value.
You can add as many parameters as you'd like.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$args` | **array** | First argument will be the name of the hook, and the rest will be args for the hook. |





***

### removeFilter

Removes a filter.

```php
public removeFilter(string $hook, mixed $callback, int $priority = 20): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$hook` | **string** | Hook name. |
| `$callback` | **mixed** | Function to execute. |
| `$priority` | **int** | Priority of the filter. |





***


***
> Automatically generated on 2025-10-13
