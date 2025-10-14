***

# RoutingServiceProvider





* Full name: `\Codefy\Framework\Providers\RoutingServiceProvider`
* Parent class: [`\Codefy\Framework\Support\CodefyServiceProvider`](../Support/CodefyServiceProvider.md)



## Properties


### loadRoutesUsing

The callback that should be used to load the application's routes.

```php
protected ?\Closure $loadRoutesUsing
```






***

### alwaysLoadRoutesUsing

The global callback that should be used to load the application's routes.

```php
protected static ?\Closure $alwaysLoadRoutesUsing
```



* This property is **static**.


***

## Methods


### register



```php
public register(): void
```












***

### routes

Register the callback that will be used to load the application's routes.

```php
protected routes(\Closure|callable|string|array|null $routes): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$routes` | **\Closure&#124;callable&#124;string&#124;array&#124;null** |  |





***

### loadRoutesUsing

Register the callback that will be used to load the application's routes.

```php
public static loadRoutesUsing(\Closure|callable|string|array|null $routes): void
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$routes` | **\Closure&#124;callable&#124;string&#124;array&#124;null** |  |





***

### loadRoutes

Load the application routes.

```php
protected loadRoutes(): void
```











**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### normalizeRoutes



```php
protected static normalizeRoutes(\Closure|callable|string|array $routes): \Closure
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$routes` | **\Closure&#124;callable&#124;string&#124;array** |  |





***

### __call

Pass dynamic methods onto the router instance.

```php
public __call(string $method, array $parameters): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$method` | **string** |  |
| `$parameters` | **array** |  |





***


## Inherited methods


### __construct



```php
public __construct(\Codefy\Framework\Application $codefy): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$codefy` | **\Codefy\Framework\Application** |  |





***

### booting

Register a booting callback to be run before the "boot" method is called.

```php
public booting(\Closure $callback): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **\Closure** |  |





***

### booted

Register a booted callback to be run after the "boot" method is called.

```php
public booted(\Closure $callback): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **\Closure** |  |





***

### callBootingCallbacks

Call the registered booting callbacks.

```php
public callBootingCallbacks(): void
```












***

### callBootedCallbacks

Call the registered booted callbacks.

```php
public callBootedCallbacks(): void
```












***

### defaultProviders

Get the default providers for a CodefyPHP application.

```php
public static defaultProviders(): \Codefy\Framework\Support\DefaultProviders
```



* This method is **static**.








***

### publishes

Register publishable paths for this provider.

```php
public publishes(array&lt;string,string&gt; $paths, string|null $group = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$paths` | **array<string,string>** | [from =&gt; tag] |
| `$group` | **string&#124;null** | Optional tag/group name (&quot;config&quot;, &quot;migrations&quot;, etc.) |





***

### pathsToPublish

Get all publishable paths for this provider.

```php
public pathsToPublish(string|null $tag = null): array&lt;string,string&gt;
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$tag` | **string&#124;null** | Restrict to a tag (e.g. &quot;config&quot;, &quot;migrations&quot;) |


**Return Value:**

[from => tag]




***

### publishTags

List all tags defined by this provider.

```php
public publishTags(): string[]
```












***


***
> Automatically generated on 2025-10-13
