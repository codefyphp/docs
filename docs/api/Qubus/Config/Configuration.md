# Configuration

***

* Full name: `\Qubus\Config\Configuration`

## Properties

### env

```php
public static array $env
```

* This property is **static**.

***

### paths

```php
protected ?\Qubus\Config\Path\PathCollection $paths
```

***

### dotenv

```php
protected ?\Dotenv\Dotenv $dotenv
```

***

### environment

```php
protected ?string $environment
```

***

## Methods

### __construct

```php
public __construct(array|\Qubus\Config\Configuration $config): mixed
```

**Parameters:**

| Parameter | Type                                   | Description |
|-----------|----------------------------------------|-------------|
| `$config` | **array\|\Qubus\Config\Configuration** |             |

**Throws:**

- [`PathNotFoundException`](./Path/PathNotFoundException.md)

***

### getPaths

```php
public getPaths(): \Qubus\Config\Path\PathCollection
```

***

### setPaths

```php
public setPaths(\Qubus\Config\Path\PathCollection $pathCollection): $this
```

**Parameters:**

| Parameter         | Type                                  | Description |
|-------------------|---------------------------------------|-------------|
| `$pathCollection` | **\Qubus\Config\Path\PathCollection** |             |

***

### setEnvironment

```php
public setEnvironment(?string $environment = null): $this
```

**Parameters:**

| Parameter      | Type        | Description |
|----------------|-------------|-------------|
| `$environment` | **?string** |             |

***

### removeEnvironment

```php
public removeEnvironment(): $this
```

***

### getEnvironment

```php
public getEnvironment(): ?string
```

***

### getDotenv

```php
public getDotenv(): ?\Dotenv\Dotenv
```

***

### setDotenv

```php
public setDotenv(\Dotenv\Dotenv $dotenv): $this
```

**Parameters:**

| Parameter | Type               | Description |
|-----------|--------------------|-------------|
| `$dotenv` | **\Dotenv\Dotenv** |             |

***

### loadDotenv

```php
private loadDotenv(): array
```

***
