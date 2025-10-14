***

# QueueableRequestHandler





* Full name: `\Qubus\Routing\Handlers\QueueableRequestHandler`
* Parent class: [`SplQueue`](../../../SplQueue.md)
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Psr\Http\Server\RequestHandlerInterface`](../../../Psr/Http/Server/RequestHandlerInterface.md)
* This class is a **Final class**



## Properties


### endpoint



```php
private \Psr\Http\Server\RequestHandlerInterface $endpoint
```






***

## Methods


### __construct



```php
public __construct(\Psr\Http\Server\RequestHandlerInterface $endpoint): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$endpoint` | **\Psr\Http\Server\RequestHandlerInterface** |  |





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
