# XmlStrategy

***

* Full name: `\Qubus\Support\Serializer\Strategy\XmlStrategy`
* This class implements:
  [`\Qubus\Support\Serializer\Strategy\Strategy`](./Strategy.md)

## Properties

### replacements

```php
private string[] $replacements
```

***

## Methods

### serialize

```php
public serialize(mixed $value): bool|string
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### replaceKeys

```php
private replaceKeys(array $replacements, array $input): array
```

**Parameters:**

| Parameter       | Type      | Description |
|-----------------|-----------|-------------|
| `$replacements` | **array** |             |
| `$input`        | **array** |             |

***

### arrayToXml

Converts an array to XML using SimpleXMLElement.

```php
private arrayToXml(array& $data, \SimpleXMLElement $xmlData): void
```

**Parameters:**

| Parameter  | Type                  | Description |
|------------|-----------------------|-------------|
| `$data`    | **array**             |             |
| `$xmlData` | **\SimpleXMLElement** |             |

***

### unserialize

```php
public unserialize(mixed $value): bool|string|array|object
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### castToArray

```php
private castToArray(array& $array): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$array`  | **array** |             |

***

### recoverArrayNumericKeyValues

```php
private recoverArrayNumericKeyValues(array& $array): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$array`  | **array** | <mixed>     |

***

### getNumericKeyValue

```php
private static getNumericKeyValue(mixed $key): int
```

* This method is **static**.
**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$key`    | **mixed** |             |

***
