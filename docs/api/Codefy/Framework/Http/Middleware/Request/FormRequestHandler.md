# FormRequestHandler

***

* Full name: `\Codefy\Framework\Http\Middleware\Request\FormRequestHandler`
* This class implements:
  `RequestHandlerInterface`
* This class is an **Abstract class**

## Properties

### middleware

```php
private \Codefy\Framework\Http\Middleware\Request\FormRequestMiddleware $middleware
```

***

## Methods

### __construct

```php
public __construct(\Codefy\Framework\Http\Middleware\Request\FormRequestMiddleware $middleware): mixed
```

**Parameters:**

| Parameter     | Type                                                                | Description |
|---------------|---------------------------------------------------------------------|-------------|
| `$middleware` | **\Codefy\Framework\Http\Middleware\Request\FormRequestMiddleware** |             |

***

### handle

```php
public handle(\Psr\Http\Message\ServerRequestInterface $request): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

***

### innerHandle

```php
protected innerHandle(\Psr\Http\Message\ServerRequestInterface $request): \Psr\Http\Message\ResponseInterface
```

* This method is **abstract**.
**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

***
