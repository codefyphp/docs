***

# SessionService





* Full name: `\Qubus\Http\Session\SessionService`


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`COOKIE_NAME`|public| |&quot;QSESSID&quot;|

## Properties


### options



```php
public static array $options
```



* This property is **static**.


***

### sessionStorage



```php
public \Qubus\Http\Session\Storage\SessionStorage $sessionStorage
```






***

### cookie



```php
public \Qubus\Http\Cookies\Factory\HttpCookieFactory $cookie
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Http\Session\Storage\SessionStorage $sessionStorage, \Qubus\Http\Cookies\Factory\HttpCookieFactory $cookie): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$sessionStorage` | **\Qubus\Http\Session\Storage\SessionStorage** |  |
| `$cookie` | **\Qubus\Http\Cookies\Factory\HttpCookieFactory** |  |





***

### makeSession

Create a Session for the given Request.

```php
public makeSession(\Psr\Http\Message\ServerRequestInterface $request): \Qubus\Http\Session\HttpSession
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |




**Throws:**

- [`Exception`](../../../Exception.md)



***

### commitSession

Commit Session to storage and add the Session Cookie to the given Response.

```php
public commitSession(\Psr\Http\Message\ResponseInterface $response, \Qubus\Http\Session\HttpSession $session): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |
| `$session` | **\Qubus\Http\Session\HttpSession** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

- [`Exception`](../../../Exception.md)

- [`InvalidArgumentException`](../../../InvalidArgumentException.md)

- [`Exception`](../../../Exception.md)



***

### getSessionLifetimeInSeconds



```php
private getSessionLifetimeInSeconds(): int
```











**Throws:**

- [`Exception`](../../../Exception.md)



***


***
> Automatically generated on 2025-10-13
