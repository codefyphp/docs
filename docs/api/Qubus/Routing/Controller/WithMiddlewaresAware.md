# WithMiddlewaresAware

***

* Full name: `\Qubus\Routing\Controller\WithMiddlewaresAware`

## Properties

### middlewares

List of controller middleware.

```php
protected array $middlewares
```

***

## Methods

### middleware

Add Middleware.

```php
public middleware(mixed $middleware): \Qubus\Routing\Controller\ControllerMiddlewareOptions
```

**Parameters:**

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `$middleware` | **mixed** |             |

***
### getControllerMiddleware

Get the array of controller middleware.

```php
public getControllerMiddleware(): array
```

***
