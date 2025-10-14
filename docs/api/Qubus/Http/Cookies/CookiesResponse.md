***

# CookiesResponse





* Full name: `\Qubus\Http\Cookies\CookiesResponse`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**




## Methods


### get



```php
public static get(\Psr\Http\Message\ResponseInterface $response, string $name, ?string $value = null): \Qubus\Http\Cookies\SetCookieCollection
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |
| `$name` | **string** |  |
| `$value` | **?string** |  |





***

### set



```php
public static set(\Psr\Http\Message\ResponseInterface $response, \Qubus\Http\Cookies\SetCookieCollection $setCookieCollection): \Psr\Http\Message\ResponseInterface
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |
| `$setCookieCollection` | **\Qubus\Http\Cookies\SetCookieCollection** |  |





***

### expire



```php
public static expire(\Psr\Http\Message\ResponseInterface $response, string $cookieName): \Psr\Http\Message\ResponseInterface
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |
| `$cookieName` | **string** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### modify



```php
public static modify(\Psr\Http\Message\ResponseInterface $response, string $name, callable $modify): \Psr\Http\Message\ResponseInterface
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |
| `$name` | **string** |  |
| `$modify` | **callable** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### remove



```php
public static remove(\Psr\Http\Message\ResponseInterface $response, string $name): \Psr\Http\Message\ResponseInterface
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |
| `$name` | **string** |  |





***


***
> Automatically generated on 2025-10-13
