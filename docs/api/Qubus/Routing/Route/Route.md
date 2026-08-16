# Route

***

* Full name: `\Qubus\Routing\Route\Route`
* This class is marked as **final** and can't be subclassed
* This class implements:
  [`\Qubus\Routing\Interfaces\Routable`](../Interfaces/Routable.md)
* This class is a **Final class**

## Properties

### uri

```php
public string $uri
```

***

### methods

```php
public array $methods
```

***

### routeAction

```php
protected \Qubus\Routing\Route\RouteAction $routeAction
```

***

### name

```php
public ?string $name
```

***

### domain

```php
protected ?string $domain
```

***

### subDomain

```php
protected ?string $subDomain
```

***

### schemes

```php
protected array $schemes
```

***

### invoker

```php
protected ?\Qubus\Routing\Invoker $invoker
```

***

### middlewareResolver

```php
protected ?\Qubus\Routing\Interfaces\MiddlewareResolver $middlewareResolver
```

***

### middlewares

```php
protected array $middlewares
```

***

### paramConstraints

```php
public array $paramConstraints
```

***

### defaultNamespace

```php
protected ?string $defaultNamespace
```

***

### namespace

```php
protected ?string $namespace
```

***

## Methods

### __construct

```php
public __construct(array $methods, string $uri, mixed $action, ?string $defaultNamespace = null, ?\Qubus\Routing\Invoker $invoker = null, ?\Qubus\Routing\Interfaces\MiddlewareResolver $middlewareResolver = null): mixed
```

**Parameters:**

| Parameter             | Type                                              | Description |
|-----------------------|---------------------------------------------------|-------------|
| `$methods`            | **array**                                         |             |
| `$uri`                | **string**                                        |             |
| `$action`             | **mixed**                                         |             |
| `$defaultNamespace`   | **?string**                                       |             |
| `$invoker`            | **?\Qubus\Routing\Invoker**                       |             |
| `$middlewareResolver` | **?\Qubus\Routing\Interfaces\MiddlewareResolver** |             |

***

### setAction

```php
protected setAction(mixed $action): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$action` | **mixed** |             |

***

### prependUrl

Prepend url

```php
public prependUrl(string $uri): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$uri`    | **string** |             |

***

### handle

```php
public handle(\Psr\Http\Message\ServerRequestInterface $request, \Qubus\Routing\Route\RouteParams $params): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |
| `$params`  | **\Qubus\Routing\Route\RouteParams**         |             |

***

### gatherMiddlewares

```php
public gatherMiddlewares(): array
```

***

### name

```php
public name(?string $name): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$name`   | **?string** |             |

**Throws:**

- [`RouteNameRedefinedException`](../Exceptions/RouteNameRedefinedException.md)

***

### domain

```php
public domain(?string $domain): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$domain` | **?string** |             |

***

### subDomain

```php
public subDomain(?string $subdomain): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter    | Type        | Description |
|--------------|-------------|-------------|
| `$subdomain` | **?string** |             |

***

### namespace

```php
public namespace(?string $namespace): \Qubus\Routing\Interfaces\Routable
```

**Parameters:**

| Parameter    | Type        | Description |
|--------------|-------------|-------------|
| `$namespace` | **?string** |             |

***

### setScheme

```php
public setScheme(string $schemes): self
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$schemes` | **string** |             |

***

### where

```php
public where(): self
```

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***

### middleware

```php
public middleware(): \Qubus\Routing\Interfaces\Routable
```

***

### getDomain

```php
public getDomain(): ?string
```

***

### getSubDomain

```php
public getSubDomain(): ?string
```

***

### getNamespace

```php
public getNamespace(): ?string
```

***

### getActionName

```php
public getActionName(): string
```

***

### getRouteAction

```php
public getRouteAction(): \Qubus\Routing\Route\RouteAction
```

***

### getSchemes

```php
public getSchemes(): ?array
```

***
