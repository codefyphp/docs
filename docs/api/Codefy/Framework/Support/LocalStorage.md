# LocalStorage

***

* Full name: `\Codefy\Framework\Support\LocalStorage`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Methods

### disk

```php
public static disk(?string $name = null): \Qubus\FileSystem\FileSystem
```

* This method is **static**.
**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$name`   | **?string** |             |

***

### getConfigForDriverName

```php
private static getConfigForDriverName(string $name): array|\Qubus\Config\ConfigContainer
```

* This method is **static**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### createInstanceOfLocalDriver

```php
public static createInstanceOfLocalDriver(string $name, (string|int|null|array)[] $configArray): \Qubus\FileSystem\FileSystem
```

* This method is **static**.
**Parameters:**

| Parameter      | Type                             | Description |
|----------------|----------------------------------|-------------|
| `$name`        | **string**                       |             |
| `$configArray` | **(string\|int\|null\|array)[]** |             |

***

### setVisibilityConverterByDiskName

```php
private static setVisibilityConverterByDiskName(string $name): array
```

* This method is **static**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***
