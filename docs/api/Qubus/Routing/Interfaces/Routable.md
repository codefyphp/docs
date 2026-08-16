# Routable

***

* Full name: `\Qubus\Routing\Interfaces\Routable`

## Methods

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
public name(?string $name): self
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$name`   | **?string** |             |

***

### domain

```php
public domain(?string $domain): self
```

**Parameters:**

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `$domain` | **?string** |             |

***

### namespace

```php
public namespace(?string $namespace): self
```

**Parameters:**

| Parameter    | Type        | Description |
|--------------|-------------|-------------|
| `$namespace` | **?string** |             |

***

### middleware

```php
public middleware(): self
```

***

### getDomain

```php
public getDomain(): ?string
```

***

### getNamespace

```php
public getNamespace(): ?string
```

***
