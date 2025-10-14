***

# LocalizationServiceProvider





* Full name: `\Codefy\Framework\Providers\LocalizationServiceProvider`
* Parent class: [`\Codefy\Framework\Support\CodefyServiceProvider`](../Support/CodefyServiceProvider.md)




## Methods


### register



```php
public register(): void
```











**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)



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
