***

# HttpCookieFactory





* Full name: `\Qubus\Http\Cookies\Factory\HttpCookieFactory`



## Methods


### make

Make a new cookie instance.

```php
public make(string $name, ?string $value = null, ?int $maxAge = null): \Qubus\Http\Cookies\SetCookieCollection
```

This method returns a cookie instance for use with the Set-Cookie HTTP header.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$value` | **?string** |  |
| `$maxAge` | **?int** |  |




**Throws:**

- [`TypeException`](../../../Exception/Data/TypeException.md)

- [`Exception`](../../../Exception/Exception.md)



***

### expire

Make an expired cookie instance.

```php
public expire(string $name): \Qubus\Http\Cookies\SetCookieCollection|string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |





***


***
> Automatically generated on 2025-10-13
