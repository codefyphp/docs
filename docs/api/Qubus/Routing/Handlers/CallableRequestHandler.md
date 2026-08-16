# CallableRequestHandler

***

* Full name: `\Qubus\Routing\Handlers\CallableRequestHandler`
* This class is marked as **final** and can't be subclassed
* This class implements:
  `RequestHandlerInterface`
* This class is a **Final class**

## Properties

### callback

```php
private callable $callback
```

***

## Methods

### __construct

```php
public __construct(callable $callback): mixed
```

**Parameters:**

| Parameter   | Type         | Description |
|-------------|--------------|-------------|
| `$callback` | **callable** |             |

***

### handle

{@inheritDoc}

```php
public handle(\Psr\Http\Message\ServerRequestInterface $request): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

***
