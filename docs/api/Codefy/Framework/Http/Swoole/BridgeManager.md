# BridgeManager

***

* Full name: `\Codefy\Framework\Http\Swoole\BridgeManager`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Properties

### app

```php
private ?\Codefy\Framework\Application $app
```

***

### responseMerger

```php
private ?\Qubus\Http\Swoole\ResponseMerger $responseMerger
```

***

### requestFactory

```php
private \Qubus\Http\Swoole\Factory\RequestFactory $requestFactory
```

***

## Methods

### __construct

```php
public __construct(\Codefy\Framework\Application $app, \Qubus\Http\Swoole\ResponseMerger $responseMerger, \Qubus\Http\Swoole\Factory\RequestFactory $requestFactory): mixed
```

**Parameters:**

| Parameter         | Type                                          | Description |
|-------------------|-----------------------------------------------|-------------|
| `$app`            | **\Codefy\Framework\Application**             |             |
| `$responseMerger` | **\Qubus\Http\Swoole\ResponseMerger**         |             |
| `$requestFactory` | **\Qubus\Http\Swoole\Factory\RequestFactory** |             |

***

### process

```php
public process(\Swoole\Http\Request $swooleRequest, \Swoole\Http\Response $swooleResponse): \Swoole\Http\Response
```

**Parameters:**

| Parameter         | Type                      | Description |
|-------------------|---------------------------|-------------|
| `$swooleRequest`  | **\Swoole\Http\Request**  |             |
| `$swooleResponse` | **\Swoole\Http\Response** |             |

**Throws:**

- [`Exception`](../../../../Exception.md)

***
