# EventDispatcherServiceProvider

***

* Full name: `\Codefy\Framework\Providers\EventDispatcherServiceProvider`
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

| Parameter | Type                              | Description |
|-----------|-----------------------------------|-------------|
| `$codefy` | **\Codefy\Framework\Application** |             |

***

### booting

Register a booting callback to be run before the "boot" method is called.

```php
public booting(\Closure $callback): void
```

**Parameters:**

| Parameter   | Type         | Description |
|-------------|--------------|-------------|
| `$callback` | **\Closure** |             |

***

### booted

Register a booted callback to be run after the "boot" method is called.

```php
public booted(\Closure $callback): void
```

**Parameters:**

| Parameter   | Type         | Description |
|-------------|--------------|-------------|
| `$callback` | **\Closure** |             |

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
public publishes(array<string,string> $paths, string|null $group = null): void
```

**Parameters:**

| Parameter | Type                     | Description                                            |
|-----------|--------------------------|--------------------------------------------------------|
| `$paths`  | **array<string,string>** | [from => tag]                                          |
| `$group`  | **string\|null**         | Optional tag/group name ("config", "migrations", etc.) |

***

### pathsToPublish

Get all publishable paths for this provider.

```php
public pathsToPublish(string|null $tag = null): array<string,string>
```

**Parameters:**

| Parameter | Type             | Description                                     |
|-----------|------------------|-------------------------------------------------|
| `$tag`    | **string\|null** | Restrict to a tag (e.g. "config", "migrations") |

**Return Value:**

[from => tag]

***

### publishTags

List all tags defined by this provider.

```php
public publishTags(): string[]
```

***
