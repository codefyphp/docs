***

# ServerRequest





* Full name: `\Qubus\Http\ServerRequest`
* Parent class: [`ServerRequest`](../../Laminas/Diactoros/ServerRequest.md)
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Psr\Http\Message\ServerRequestInterface`](../../Psr/Http/Message/ServerRequestInterface.md)
* This class is a **Final class**




## Methods


### __construct



```php
public __construct(array $serverParams = [], array $uploadedFiles = [], mixed $uri = null, ?string $method = null, mixed $body = &#039;php://input&#039;, array $headers = [], array $cookies = [], array $queryParams = [], mixed $parsedBody = null, string $protocol = &#039;1.1&#039;): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$serverParams` | **array** |  |
| `$uploadedFiles` | **array** |  |
| `$uri` | **mixed** |  |
| `$method` | **?string** |  |
| `$body` | **mixed** |  |
| `$headers` | **array** |  |
| `$cookies` | **array** |  |
| `$queryParams` | **array** |  |
| `$parsedBody` | **mixed** |  |
| `$protocol` | **string** |  |





***

### get



```php
public get(mixed $name): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |





***


***
> Automatically generated on 2025-10-13
