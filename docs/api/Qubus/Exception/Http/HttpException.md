# HttpException

***

* Full name: `\Qubus\Exception\Http\HttpException`
* Parent class: [`RuntimeException`](../../../RuntimeException.md)
* This class implements:
  [`\Qubus\Exception\Http\Psr7Exception`](./Psr7Exception.md)

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
