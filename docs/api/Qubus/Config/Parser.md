***

# Parser





* Full name: `\Qubus\Config\Parser`




## Methods


### getKey



```php
public static getKey(string $name): array
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***

### getValue



```php
public static getValue(array|null $haystack = null, string|null $key = null, null|array $sub = null, mixed|null $default = null): mixed
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$haystack` | **array&#124;null** |  |
| `$key` | **string&#124;null** |  |
| `$sub` | **null&#124;array** |  |
| `$default` | **mixed&#124;null** |  |





***

### findInMultiArray



```php
private static findInMultiArray(array $needle, array $haystack): mixed
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$needle` | **array** |  |
| `$haystack` | **array** |  |





***


***
> Automatically generated on 2025-10-13
