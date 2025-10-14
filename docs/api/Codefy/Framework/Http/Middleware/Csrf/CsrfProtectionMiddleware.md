***

# CsrfProtectionMiddleware





* Full name: `\Codefy\Framework\Http\Middleware\Csrf\CsrfProtectionMiddleware`
* This class implements:
[`\Psr\Http\Server\MiddlewareInterface`](../../../../../Psr/Http/Server/MiddlewareInterface.md)



## Properties


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

### needsProtection

Check for methods not defined as safe.

```php
private needsProtection(\Psr\Http\Message\ServerRequestInterface $request): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |





***

### tokensMatch



```php
private tokensMatch(\Psr\Http\Message\ServerRequestInterface $request): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |




**Throws:**

- [`Exception`](../../../../../Qubus/Exception/Exception.md)



***

### fetchToken



```php
private fetchToken(\Psr\Http\Message\ServerRequestInterface $request): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |




**Throws:**

- [`Exception`](../../../../../Qubus/Exception/Exception.md)

- [`Exception`](../../../../../Exception.md)



***

### getTokenFromRequest



```php
private getTokenFromRequest(\Psr\Http\Message\ServerRequestInterface $request): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |




**Throws:**

- [`Exception`](../../../../../Qubus/Exception/Exception.md)



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
