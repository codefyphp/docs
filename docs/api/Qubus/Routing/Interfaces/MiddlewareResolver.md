# MiddlewareResolver

***

* Full name: `\Qubus\Routing\Interfaces\MiddlewareResolver`

## Methods

### resolve

Resolves a middleware

```php
public resolve(mixed $definition): \Psr\Http\Server\MiddlewareInterface|callable
```

**Parameters:**

| Parameter     | Type      | Description                      |
|---------------|-----------|----------------------------------|
| `$definition` | **mixed** | The key to look up a middleware. |

***
