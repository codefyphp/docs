# GateMiddleware

***

* Full name: `\Codefy\Framework\Http\Middleware\Auth\GateMiddleware`
* This class is marked as **final** and can't be subclassed
* This class implements:
  `MiddlewareInterface`
* This class is a **Final class**

## Properties

### permission

```php
private ?string $permission
```

***

### redirect

```php
private ?string $redirect
```

***

### redirectIfAuthorized

```php
private bool|string $redirectIfAuthorized
```

***

### user

```php
private \Codefy\Framework\Auth\Gate $user
```

***

### configContainer

```php
private \Qubus\Config\ConfigContainer $configContainer
```

***

## Methods

### __construct

```php
public __construct(\Codefy\Framework\Auth\Gate $user, \Qubus\Config\ConfigContainer $configContainer): mixed
```

**Parameters:**

| Parameter          | Type                              | Description |
|--------------------|-----------------------------------|-------------|
| `$user`            | **\Codefy\Framework\Auth\Gate**   |             |
| `$configContainer` | **\Qubus\Config\ConfigContainer** |             |

***

### withArguments

```php
public withArguments(?string $permission = null, ?string $redirect = null, bool|string $redirectIfAuthorized = false): self
```

**Parameters:**

| Parameter               | Type             | Description |
|-------------------------|------------------|-------------|
| `$permission`           | **?string**      |             |
| `$redirect`             | **?string**      |             |
| `$redirectIfAuthorized` | **bool\|string** |             |

***

### process

```php
public process(\Psr\Http\Message\ServerRequestInterface $request, \Psr\Http\Server\RequestHandlerInterface $handler): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |
| `$handler` | **\Psr\Http\Server\RequestHandlerInterface** |             |

**Throws:**

- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)
- [`Exception`](../../../../../Exception.md)

***
