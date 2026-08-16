# RequestFactory

***

* Full name: `\Qubus\Http\Swoole\Factory\RequestFactory`
* This class implements:
  [`\Qubus\Http\Swoole\Factory\PsrSwooleFactory`](./PsrSwooleFactory.md)

## Properties

### uriFactory

```php
private \Psr\Http\Message\UriFactoryInterface $uriFactory
```

***

### streamFactory

```php
private \Psr\Http\Message\StreamFactoryInterface $streamFactory
```

***

### uploadedFileFactory

```php
private \Psr\Http\Message\UploadedFileFactoryInterface $uploadedFileFactory
```

***

## Methods

### __construct

```php
public __construct(\Psr\Http\Message\UriFactoryInterface $uriFactory, \Psr\Http\Message\StreamFactoryInterface $streamFactory, \Psr\Http\Message\UploadedFileFactoryInterface $uploadedFileFactory): mixed
```

**Parameters:**

| Parameter              | Type                                               | Description |
|------------------------|----------------------------------------------------|-------------|
| `$uriFactory`          | **\Psr\Http\Message\UriFactoryInterface**          |             |
| `$streamFactory`       | **\Psr\Http\Message\StreamFactoryInterface**       |             |
| `$uploadedFileFactory` | **\Psr\Http\Message\UploadedFileFactoryInterface** |             |

***

### createRequest

```php
public createRequest(\Swoole\Http\Request $swooleRequest): \Qubus\Http\Swoole\Request
```

**Parameters:**

| Parameter        | Type                     | Description |
|------------------|--------------------------|-------------|
| `$swooleRequest` | **\Swoole\Http\Request** |             |

***

### createServerRequest

```php
public createServerRequest(\Swoole\Http\Request $swooleRequest): \Psr\Http\Message\ServerRequestInterface
```

**Parameters:**

| Parameter        | Type                     | Description |
|------------------|--------------------------|-------------|
| `$swooleRequest` | **\Swoole\Http\Request** |             |

***
