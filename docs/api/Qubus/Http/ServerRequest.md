# ServerRequest

***

* Full name: `\Qubus\Http\ServerRequest`
* Parent class: [`ServerRequest`](../../Laminas/Diactoros/ServerRequest.md)
* This class implements:
  `ServerRequestInterface`

## Methods

### __construct

```php
public __construct(array $serverParams = [], array $uploadedFiles = [], mixed $uri = null, ?string $method = null, mixed $body = 'php://input', array $headers = [], array $cookies = [], array $queryParams = [], mixed $parsedBody = null, string $protocol = '1.1'): mixed
```

**Parameters:**

| Parameter        | Type        | Description |
|------------------|-------------|-------------|
| `$serverParams`  | **array**   |             |
| `$uploadedFiles` | **array**   |             |
| `$uri`           | **mixed**   |             |
| `$method`        | **?string** |             |
| `$body`          | **mixed**   |             |
| `$headers`       | **array**   |             |
| `$cookies`       | **array**   |             |
| `$queryParams`   | **array**   |             |
| `$parsedBody`    | **mixed**   |             |
| `$protocol`      | **string**  |             |

***

### get

```php
public get(mixed $name): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$name`   | **mixed** |             |

***
