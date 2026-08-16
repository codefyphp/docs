# PresetRegistry

***

* Full name: `\Codefy\Framework\Console\PresetRegistry`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Properties

### configContainer

```php
protected \Qubus\Config\ConfigContainer $configContainer
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Config\ConfigContainer $configContainer): mixed
```

**Parameters:**

| Parameter          | Type                              | Description |
|--------------------|-----------------------------------|-------------|
| `$configContainer` | **\Qubus\Config\ConfigContainer** |             |

***

### all

```php
public all(): array<array-key,array>
```

**Throws:**

- [`Exception`](../../../Exception.md)

***

### get

```php
public get(string $key): array<array-key,array>
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

**Throws:**

- [`Exception`](../../../Exception.md)

***

### stubsPath

```php
public stubsPath(): string
```

**Throws:**

- [`Exception`](../../../Exception.md)

***
