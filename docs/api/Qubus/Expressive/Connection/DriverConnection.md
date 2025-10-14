***

# DriverConnection





* Full name: `\Qubus\Expressive\Connection\DriverConnection`




## Methods


### make

Build a driver-native connection (extension-specific).

```php
public static make(array|string $config): \Qubus\Expressive\Connection
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$config` | **array&#124;string** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### parseDsn

Parse a DSN-like URL into config array.

```php
protected static parseDsn(string $url): array
```

Example: mysql://user:pass@localhost:3306/dbname?charset=utf8mb4

* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$url` | **string** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***


***
> Automatically generated on 2025-10-13
