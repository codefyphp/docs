# YamlLoader

***

* Full name: `\Qubus\Config\Loader\YamlLoader`
* This class implements:
  [`\Qubus\Config\Loader\Loader`](./Loader.md)

## Constants

| Constant    | Visibility | Type | Value  |
|-------------|------------|------|--------|
| `EXTENSION` | public     |      | 'yaml' |

## Properties

### parser

```php
protected static ?\Symfony\Component\Yaml\Parser $parser
```

* This property is **static**.

***

## Methods

### getParser

Gets the parser to parse YAML strings to PHP arrays.

```php
protected static getParser(): \Symfony\Component\Yaml\Parser
```

* This method is **static**.
***

### load

Loads the config file.

```php
public static load(string $file): mixed
```

* This method is **static**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$file`   | **string** |             |

***
