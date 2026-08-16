# DefaultCommands

***

* Full name: `\Codefy\Framework\Support\DefaultCommands`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Methods

### __construct

```php
public __construct((class-string<\Symfony\Component\Console\Command\SignalableCommandInterface>|callable)[] $collection = []): mixed
```

**Parameters:**

| Parameter     | Type                                                                                          | Description |
|---------------|-----------------------------------------------------------------------------------------------|-------------|
| `$collection` | **(class-string<\Symfony\Component\Console\Command\SignalableCommandInterface>\|callable)[]** |             |

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
