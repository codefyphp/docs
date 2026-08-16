# ResponseMerger

***

* Full name: `\Qubus\Http\Swoole\ResponseMerger`

## Constants

| Constant             | Visibility | Type | Value       |
|----------------------|------------|------|-------------|
| `FSTAT_MODE_S_IFIFO` | public     |      | 010000      |
| `BUFFER_SIZE`        | public     |      | 8192        |
| `FILES_STREAM_TYPE`  | protected  |      | 'STDIO'     |
| `FILES_WRAPPER_TYPE` | protected  |      | 'plainfile' |

## Methods

### toSwoole

```php
public toSwoole(\Psr\Http\Message\ResponseInterface $psrResponse, \Swoole\Http\Response $swooleResponse): \Swoole\Http\Response
```

**Parameters:**

| Parameter         | Type                                    | Description |
|-------------------|-----------------------------------------|-------------|
| `$psrResponse`    | **\Psr\Http\Message\ResponseInterface** |             |
| `$swooleResponse` | **\Swoole\Http\Response**               |             |

***

### copyHeaders

```php
private copyHeaders(mixed $psrResponse, mixed $swooleResponse): void
```

**Parameters:**

| Parameter         | Type      | Description |
|-------------------|-----------|-------------|
| `$psrResponse`    | **mixed** |             |
| `$swooleResponse` | **mixed** |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***

### setCookies

```php
private setCookies(mixed $swooleResponse, mixed $psrResponse): void
```

**Parameters:**

| Parameter         | Type      | Description |
|-------------------|-----------|-------------|
| `$swooleResponse` | **mixed** |             |
| `$psrResponse`    | **mixed** |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***

### getSameSiteModifier

```php
private getSameSiteModifier(mixed $setCookie): string
```

**Parameters:**

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `$setCookie` | **mixed** |             |

***

### copyBody

```php
private copyBody(mixed $psrResponse, mixed $swooleResponse): void
```

**Parameters:**

| Parameter         | Type      | Description |
|-------------------|-----------|-------------|
| `$psrResponse`    | **mixed** |             |
| `$swooleResponse` | **mixed** |             |

***

### copyBodyIfIsAPipe

```php
private copyBodyIfIsAPipe(mixed $psrResponse, mixed $swooleResponse): void
```

**Parameters:**

| Parameter         | Type      | Description |
|-------------------|-----------|-------------|
| `$psrResponse`    | **mixed** |             |
| `$swooleResponse` | **mixed** |             |

***

### isPipe

```php
private isPipe(mixed $resource): bool
```

**Parameters:**

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `$resource` | **mixed** |             |

***

### isFileStreamInBody

```php
private isFileStreamInBody(\Psr\Http\Message\ResponseInterface $psrResponse): bool
```

**Parameters:**

| Parameter      | Type                                    | Description |
|----------------|-----------------------------------------|-------------|
| `$psrResponse` | **\Psr\Http\Message\ResponseInterface** |             |

***
