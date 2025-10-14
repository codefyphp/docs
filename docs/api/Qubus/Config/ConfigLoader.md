***

# ConfigLoader





* Full name: `\Qubus\Config\ConfigLoader`



## Properties


### loaders



```php
protected static array $loaders
```



* This property is **static**.


***

## Methods


### load



```php
public static load(\Qubus\Config\Path\PathCollection $paths, string|null $env, string $file): array
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$paths` | **\Qubus\Config\Path\PathCollection** |  |
| `$env` | **string&#124;null** |  |
| `$file` | **string** |  |





***

### loadFile



```php
public static loadFile(string|\Qubus\Config\Path\PathCollection $path, string|null $env, string $file): array
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **string&#124;\Qubus\Config\Path\PathCollection** |  |
| `$env` | **string&#124;null** |  |
| `$file` | **string** |  |





***

### mergeArrays



```php
public static mergeArrays(array $array1, array $array2, array|null $array3 = null): array
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array1` | **array** |  |
| `$array2` | **array** |  |
| `$array3` | **array&#124;null** |  |





***


***
> Automatically generated on 2025-10-13
