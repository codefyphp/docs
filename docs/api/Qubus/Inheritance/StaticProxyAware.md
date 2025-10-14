***

# StaticProxyAware





* Full name: `\Qubus\Inheritance\StaticProxyAware`



## Properties


### instance

The stored singleton instance.

```php
protected static self $instance
```



* This property is **static**.


***

## Methods


### getInstance

Creates the original or retrieves the stored singleton instance.

```php
public static getInstance(): self
```



* This method is **static**.







**Throws:**

- [`ReflectionException`](../../ReflectionException.md)



***

### resetInstance

Reset the Container instance.

```php
public static resetInstance(): void
```



* This method is **static**.








***

### __construct

The constructor is disabled.

```php
public __construct(): mixed
```











**Throws:**
<p>If called..</p>

- [`RuntimeException`](../../RuntimeException.md)



***

### __clone

Cloning is disabled.

```php
public __clone(): mixed
```











**Throws:**
<p>If called.</p>

- [`RuntimeException`](../../RuntimeException.md)



***

### __wakeup

Wakeup is disabled.

```php
public __wakeup(): mixed
```











**Throws:**
<p>If called.</p>

- [`RuntimeException`](../../RuntimeException.md)



***

### unserialize

Unserialization is disabled.

```php
public unserialize(array $serializedData): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$serializedData` | **array** |  |




**Throws:**
<p>If called.</p>

- [`RuntimeException`](../../RuntimeException.md)



***

***
> Automatically generated on 2025-10-13

