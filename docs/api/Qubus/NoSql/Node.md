***

# Node





* Full name: `\Qubus\NoSql\Node`



## Properties


### collections



```php
protected static array $collections
```



* This property is **static**.


***

### macros



```php
protected static array $macros
```



* This property is **static**.


***

## Methods


### open

Opens a file.

```php
public static open(string $file, array $options = []): \Qubus\NoSql\Collection
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$file` | **string** | The file to open. |
| `$options` | **array** |  |





***

### macro

Create a macro.

```php
public static macro(string $name, callable $callback): void
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | Name of the macro. |
| `$callback` | **callable** |  |





***


***
> Automatically generated on 2025-10-13
