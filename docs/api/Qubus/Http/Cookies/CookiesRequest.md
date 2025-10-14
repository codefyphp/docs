***

# CookiesRequest





* Full name: `\Qubus\Http\Cookies\CookiesRequest`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**




## Methods


### get



```php
public static get(\Psr\Http\Message\RequestInterface $request, string $name, ?string $value = null): \Qubus\Http\Cookies\CookieCollection
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\RequestInterface** |  |
| `$name` | **string** |  |
| `$value` | **?string** |  |





***

### set



```php
public static set(\Psr\Http\Message\RequestInterface $request, \Qubus\Http\Cookies\CookieCollection $cookie): \Psr\Http\Message\RequestInterface
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\RequestInterface** |  |
| `$cookie` | **\Qubus\Http\Cookies\CookieCollection** |  |





***

### modify



```php
public static modify(\Psr\Http\Message\RequestInterface $request, string $name, callable $modify): \Psr\Http\Message\RequestInterface
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\RequestInterface** |  |
| `$name` | **string** |  |
| `$modify` | **callable** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### remove



```php
public static remove(\Psr\Http\Message\RequestInterface $request, string $name): \Psr\Http\Message\RequestInterface
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\RequestInterface** |  |
| `$name` | **string** |  |





***


***
> Automatically generated on 2025-10-13
