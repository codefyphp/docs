# DefaultProviders

***

* Full name: `\Codefy\Framework\Support\DefaultProviders`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Methods

### __construct

```php
public __construct((\Qubus\Injector\ServiceProvider\Serviceable|\Qubus\Injector\ServiceProvider\Bootable)[] $collection = []): mixed
```

**Parameters:**

| Parameter     | Type                                                                                          | Description |
|---------------|-----------------------------------------------------------------------------------------------|-------------|
| `$collection` | **(\Qubus\Injector\ServiceProvider\Serviceable\|\Qubus\Injector\ServiceProvider\Bootable)[]** |             |

***

## Inherited methods

### merge

Merge the given collection into another collection.

```php
public merge(array $collection): static
```

**Parameters:**

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `$collection` | **array** |             |

***

### replace

Replace the given collection with other collections.

```php
public replace(array $replacements): static
```

**Parameters:**

| Parameter       | Type      | Description |
|-----------------|-----------|-------------|
| `$replacements` | **array** |             |

***

### except

Disable the given collection.

```php
public except(array $collection): static
```

**Parameters:**

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `$collection` | **array** |             |

***

### toArray

Convert the collection to an array.

```php
public toArray(): array
```

***
