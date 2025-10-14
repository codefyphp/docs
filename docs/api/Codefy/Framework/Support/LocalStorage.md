***

# LocalStorage





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

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **?string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### getConfigForDriverName



```php
private static getConfigForDriverName(string $name): array|\Qubus\Config\ConfigContainer
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### createInstanceOfLocalDriver



```php
public static createInstanceOfLocalDriver(string $name, array $configArray): \Qubus\FileSystem\FileSystem
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$configArray` | **array** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### setVisibilityConverterByDiskName



```php
private static setVisibilityConverterByDiskName(string $name): array
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***


***
> Automatically generated on 2025-10-13
