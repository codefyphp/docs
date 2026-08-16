# FoilView

***

* Full name: `\Codefy\Framework\View\FoilView`
* This class is marked as **final** and can't be subclassed
* This class implements:
  `Renderer`
* This class is a **Final class**

## Properties

### engine

```php
private \Foil\Engine $engine
```

***

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

**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)
- [`Exception`](../../../Qubus/Exception/Exception.md)

***

### render

```php
public render(array|string $template, array $data = []): string
```

**Parameters:**

| Parameter   | Type              | Description |
|-------------|-------------------|-------------|
| `$template` | **array\|string** |             |
| `$data`     | **array**         |             |

***
