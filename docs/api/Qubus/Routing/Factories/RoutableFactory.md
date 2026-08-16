# RoutableFactory

***

* Full name: `\Qubus\Routing\Factories\RoutableFactory`

## Methods

### create

```php
public static create(array $methods, string $uri, mixed $action, ?string $defaultNamespace = null, ?\Invoker\InvokerInterface $invoker = null, ?\Qubus\Routing\Interfaces\MiddlewareResolver $middlewareResolver = null): \Qubus\Routing\Route\Route
```

* This method is **static**.
**Parameters:**

| Parameter             | Type                                              | Description |
|-----------------------|---------------------------------------------------|-------------|
| `$methods`            | **array**                                         |             |
| `$uri`                | **string**                                        |             |
| `$action`             | **mixed**                                         |             |
| `$defaultNamespace`   | **?string**                                       |             |
| `$invoker`            | **?\Invoker\InvokerInterface**                    |             |
| `$middlewareResolver` | **?\Qubus\Routing\Interfaces\MiddlewareResolver** |             |

***
