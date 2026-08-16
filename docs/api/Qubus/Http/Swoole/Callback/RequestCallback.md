# RequestCallback

***

* Full name: `\Qubus\Http\Swoole\Callback\RequestCallback`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Properties

### handler

```php
private \Psr\Http\Server\RequestHandlerInterface $handler
```

***

### options

```php
private \Qubus\Http\Swoole\Callback\RequestCallbackOptions $options
```

***

## Methods

### fromCallable

```php
public static fromCallable(callable $callable, \Qubus\Http\Swoole\Callback\RequestCallbackOptions|null $options = null): static
```

* This method is **static**.
**Parameters:**

| Parameter   | Type                                                         | Description |
|-------------|--------------------------------------------------------------|-------------|
| `$callable` | **callable**                                                 |             |
| `$options`  | **\Qubus\Http\Swoole\Callback\RequestCallbackOptions\|null** |             |

***

### __construct

```php
public __construct(\Psr\Http\Server\RequestHandlerInterface $handler, ?\Qubus\Http\Swoole\Callback\RequestCallbackOptions $options = null): mixed
```

**Parameters:**

| Parameter  | Type                                                    | Description |
|------------|---------------------------------------------------------|-------------|
| `$handler` | **\Psr\Http\Server\RequestHandlerInterface**            |             |
| `$options` | **?\Qubus\Http\Swoole\Callback\RequestCallbackOptions** |             |

***

### __invoke

```php
public __invoke(\Swoole\Http\Request $request, \Swoole\Http\Response $response): void
```

**Parameters:**

| Parameter   | Type                      | Description |
|-------------|---------------------------|-------------|
| `$request`  | **\Swoole\Http\Request**  |             |
| `$response` | **\Swoole\Http\Response** |             |

***

### createServerRequest

```php
private createServerRequest(\Swoole\Http\Request $swooleRequest): \Psr\Http\Message\ServerRequestInterface
```

**Parameters:**

| Parameter        | Type                     | Description |
|------------------|--------------------------|-------------|
| `$swooleRequest` | **\Swoole\Http\Request** |             |

***

### emit

```php
private emit(\Psr\Http\Message\ResponseInterface $psrResponse, \Swoole\Http\Response $swooleResponse): void
```

**Parameters:**

| Parameter         | Type                                    | Description |
|-------------------|-----------------------------------------|-------------|
| `$psrResponse`    | **\Psr\Http\Message\ResponseInterface** |             |
| `$swooleResponse` | **\Swoole\Http\Response**               |             |

***
