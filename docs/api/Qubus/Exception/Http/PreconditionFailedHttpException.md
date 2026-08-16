# PreconditionFailedHttpException

***

* Full name: `\Qubus\Exception\Http\PreconditionFailedHttpException`
* Parent class: [`\Qubus\Exception\Http\HttpException`](./HttpException.md)

## Methods

### __construct

```php
public __construct(\Psr\Http\Message\UriInterface|string|null $uri = null, string $message = 'Precondition Failed', ?\Throwable $previous = null): mixed
```

**Parameters:**

| Parameter   | Type                                             | Description |
|-------------|--------------------------------------------------|-------------|
| `$uri`      | **\Psr\Http\Message\UriInterface\|string\|null** |             |
| `$message`  | **string**                                       |             |
| `$previous` | **?\Throwable**                                  |             |

***

## Inherited methods

### __construct

```php
public __construct(\Psr\Http\Message\UriInterface|string|null $uri = null, string $message = '', mixed $code = 0, ?\Throwable $previous = null): mixed
```

**Parameters:**

| Parameter   | Type                                             | Description |
|-------------|--------------------------------------------------|-------------|
| `$uri`      | **\Psr\Http\Message\UriInterface\|string\|null** |             |
| `$message`  | **string**                                       |             |
| `$code`     | **mixed**                                        |             |
| `$previous` | **?\Throwable**                                  |             |

***

### getUri

Return the uri to redirect to.

```php
public getUri(): \Psr\Http\Message\UriInterface|string|null
```

***
