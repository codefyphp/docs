# ClassGenerator

***

* Full name: `\Codefy\Framework\Console\ClassGenerator`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Properties

### codefy

```php
protected \Codefy\Framework\Application $codefy
```

***

### configContainer

```php
protected \Qubus\Config\ConfigContainer $configContainer
```

***

### filesystem

```php
protected \Qubus\FileSystem\FileSystem $filesystem
```

***

## Methods

### __construct

```php
public __construct(\Codefy\Framework\Application $codefy, \Qubus\Config\ConfigContainer $configContainer, \Qubus\FileSystem\FileSystem $filesystem): mixed
```

**Parameters:**

| Parameter          | Type                              | Description |
|--------------------|-----------------------------------|-------------|
| `$codefy`          | **\Codefy\Framework\Application** |             |
| `$configContainer` | **\Qubus\Config\ConfigContainer** |             |
| `$filesystem`      | **\Qubus\FileSystem\FileSystem**  |             |

***

### generate

Generate class files from a preset.

```php
public generate(array $preset, string $namespace, string $directory, string $className, string|null $overridePath = null): array
```

**Parameters:**

| Parameter       | Type             | Description |
|-----------------|------------------|-------------|
| `$preset`       | **array**        |             |
| `$namespace`    | **string**       |             |
| `$directory`    | **string**       |             |
| `$className`    | **string**       |             |
| `$overridePath` | **string\|null** |             |

**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)

***
