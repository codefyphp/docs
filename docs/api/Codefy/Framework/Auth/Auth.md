***

# Auth





* Full name: `\Codefy\Framework\Auth\Auth`
* This class implements:
[`\Codefy\Framework\Auth\Sentinel`](./Sentinel.md)



## Properties


### repository



```php
protected \Codefy\Framework\Auth\Repository\AuthUserRepository $repository
```






***

### configContainer



```php
protected \Qubus\Config\ConfigContainer $configContainer
```






***

### rbac



```php
protected \Codefy\Framework\Auth\Rbac\Rbac $rbac
```






***

### responseFactory



```php
protected \Psr\Http\Message\ResponseFactoryInterface $responseFactory
```






***

## Methods


### __construct



```php
public __construct(\Codefy\Framework\Auth\Repository\AuthUserRepository $repository, \Qubus\Config\ConfigContainer $configContainer, \Codefy\Framework\Auth\Rbac\Rbac $rbac, \Psr\Http\Message\ResponseFactoryInterface $responseFactory): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$repository` | **\Codefy\Framework\Auth\Repository\AuthUserRepository** |  |
| `$configContainer` | **\Qubus\Config\ConfigContainer** |  |
| `$rbac` | **\Codefy\Framework\Auth\Rbac\Rbac** |  |
| `$responseFactory` | **\Psr\Http\Message\ResponseFactoryInterface** |  |





***

### authenticate

Authenticates user if the user exists.

```php
public authenticate(\Psr\Http\Message\ServerRequestInterface $request): \Qubus\Http\Session\SessionEntity|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |




**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)



***

### unauthorized

If user does not exist, return an unauthorized response.

```php
public unauthorized(\Psr\Http\Message\ServerRequestInterface $request): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |




**Throws:**

- [`Exception`](../../../Exception.md)



***


***
> Automatically generated on 2025-10-13
