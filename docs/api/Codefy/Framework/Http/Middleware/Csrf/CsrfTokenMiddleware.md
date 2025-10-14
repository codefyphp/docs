***

# CsrfTokenMiddleware





* Full name: `\Codefy\Framework\Http\Middleware\Csrf\CsrfTokenMiddleware`
* This class implements:
[`\Psr\Http\Server\MiddlewareInterface`](../../../../../Psr/Http/Server/MiddlewareInterface.md)


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`CSRF_SESSION_ATTRIBUTE`|public| |&#039;CSRF_TOKEN&#039;|

## Properties


### current



```php
public static \Codefy\Framework\Http\Middleware\Csrf\CsrfTokenMiddleware $current
```



* This property is **static**.


***

### token



```php
private ?string $token
```






***

### configContainer



```php
protected \Qubus\Config\ConfigContainer $configContainer
```






***

### sessionService



```php
protected \Qubus\Http\Session\SessionService $sessionService
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Config\ConfigContainer $configContainer, \Qubus\Http\Session\SessionService $sessionService): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$configContainer` | **\Qubus\Config\ConfigContainer** |  |
| `$sessionService` | **\Qubus\Http\Session\SessionService** |  |





***

### getField



```php
public static getField(): string
```



* This method is **static**.







**Throws:**

- [`Exception`](../../../../../Qubus/Exception/Exception.md)



***

### getFieldAttr



```php
public getFieldAttr(): string
```











**Throws:**

- [`Exception`](../../../../../Qubus/Exception/Exception.md)



***

### process



```php
public process(\Psr\Http\Message\ServerRequestInterface $request, \Psr\Http\Server\RequestHandlerInterface $handler): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |
| `$handler` | **\Psr\Http\Server\RequestHandlerInterface** |  |





***


## Inherited methods


### generateToken



```php
protected generateToken(): string
```











**Throws:**

- [`Exception`](../../../../../Qubus/Exception/Exception.md)



***

### prepareToken



```php
protected prepareToken(\Qubus\Http\Session\HttpSession $session): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$session` | **\Qubus\Http\Session\HttpSession** |  |




**Throws:**

- [`Exception`](../../../../../Qubus/Exception/Exception.md)



***

### hashEquals



```php
protected hashEquals(string $knownString, string $userString): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$knownString` | **string** |  |
| `$userString` | **string** |  |




**Throws:**

- [`Exception`](../../../../../Qubus/Exception/Exception.md)



***


***
> Automatically generated on 2025-10-13
