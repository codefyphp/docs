# ValidationException

***

* Full name: `\Qubus\Validation\ValidationException`
* Parent class: [`HttpException`](../Exception/Http/HttpException.md)

## Properties

### uri

```php
protected \Psr\Http\Message\UriInterface|string|null $uri
```

***

### code

```php
protected $code
```

***

## Methods

### __construct

```php
public __construct(\Psr\Http\Message\UriInterface|string|null $uri = null, string $message = '', mixed $code = 400, ?\Throwable $previous = null): mixed
```

**Parameters:**

| Parameter   | Type                                             | Description |
|-------------|--------------------------------------------------|-------------|
| `$uri`      | **\Psr\Http\Message\UriInterface\|string\|null** |             |
| `$message`  | **string**                                       |             |
| `$code`     | **mixed**                                        |             |
| `$previous` | **?\Throwable**                                  |             |

***
