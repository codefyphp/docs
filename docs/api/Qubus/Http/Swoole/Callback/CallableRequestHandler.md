***

# CallableRequestHandler





* Full name: `\Qubus\Http\Swoole\Callback\CallableRequestHandler`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Psr\Http\Server\RequestHandlerInterface`](../../../../Psr/Http/Server/RequestHandlerInterface.md)
* This class is a **Final class**



## Properties


### callable



```php
private callable $callable
```






***

## Methods


### __construct



```php
public __construct(callable $callable): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callable` | **callable** |  |





***

### handle



```php
public handle(\Psr\Http\Message\ServerRequestInterface $request): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |





***


***
> Automatically generated on 2025-10-13
