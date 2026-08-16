# Url

***

* Full name: `\Qubus\Http\Url`
* Parent class: [`Uri`](../../Laminas/Diactoros/Uri.md)
* This class implements:
  `UriInterface`,
  `JsonSerializable`

## Properties

### originalUrl

```php
public null|string $originalUrl
```

***

### scheme

```php
private string $scheme
```

***

### username

```php
public ?string $username
```

***

### password

```php
private ?string $password
```

***

### host

```php
private string $host
```

***

### port

```php
private ?int $port
```

***

### path

```php
private string $path
```

***

### originalPath

Original path with no sanitization to ending slash.

```php
private string|null $originalPath
```

***

### params

```php
private array $params
```

***

### fragment

```php
private string $fragment
```

***

## Methods

### __construct

```php
public __construct(string $uri = ''): mixed
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$uri`    | **string** |             |

**Throws:**

- [`MalformedUrlException`](./Exception/MalformedUrlException.md)

***

### parse

```php
public parse(?string $url = null, bool $originalPath = false): self
```

**Parameters:**

| Parameter       | Type        | Description |
|-----------------|-------------|-------------|
| `$url`          | **?string** |             |
| `$originalPath` | **bool**    |             |

**Throws:**

- [`MalformedUrlException`](./Exception/MalformedUrlException.md)

***

### isSecure

Check if url is using a secure protocol like https.

```php
public isSecure(): bool
```

***

### isRelative

Checks if url is relative.

```php
public isRelative(): bool
```

***

### withUsername

Set the username of the url

```php
public withUsername(string $username): static
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$username` | **string** |             |

***

### withPassword

Set the url password

```php
public withPassword(string $password): static
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$password` | **string** |             |

***

### withPath

Set the url path

```php
public withPath(string $path): static
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$path`   | **string** |             |

***

### mergeParams

Merge parameters array

```php
public mergeParams(array $params): static
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$params` | **array** |             |

***

### withParams

Set the url params

```php
public withParams(array $params): static
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$params` | **array** |             |

***

### withQueryString

Set raw query-string parameters as string

```php
public withQueryString(string $queryString): static
```

**Parameters:**

| Parameter      | Type       | Description |
|----------------|------------|-------------|
| `$queryString` | **string** |             |

***

### getQueryString

Get query-string params as string

```php
public getQueryString(): string
```

***

### getFragment

Get fragment from url (everything after #)

```php
public getFragment(): string
```

***

### indexOf

Get position of value.

```php
public indexOf(string $value): int
```

Returns -1 on failure.

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$value`  | **string** |             |

***

### contains

Check if url contains value.

```php
public contains(string $value): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$value`  | **string** |             |

***

### hasParam

Check if url contains parameter/query string.

```php
public hasParam(string $name): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### removeParams

Removes multiple parameters from the query-string

```php
public removeParams(int[]|string[] $names): static
```

**Parameters:**

| Parameter | Type                | Description |
|-----------|---------------------|-------------|
| `$names`  | **int[]\|string[]** |             |

***

### removeParam

Removes parameter from the query-string

```php
public removeParam(string $name): static
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### getParam

Get parameter by name.

```php
public getParam(string $name, ?string $defaultValue = null): ?string
```

Returns parameter value or default value.

**Parameters:**

| Parameter       | Type        | Description |
|-----------------|-------------|-------------|
| `$name`         | **string**  |             |
| `$defaultValue` | **?string** |             |

***

### parseUrl

UTF-8 aware parse_url() replacement.

```php
public parseUrl(string $url, int $component = -1): array
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$url`       | **string** |             |
| `$component` | **int**    |             |

**Throws:**

- [`MalformedUrlException`](./Exception/MalformedUrlException.md)

***

### arrayToParams

Convert array to query-string params.

```php
public static arrayToParams(array $getParams = [], bool $includeEmpty = true): string
```

* This method is **static**.
**Parameters:**

| Parameter       | Type      | Description |
|-----------------|-----------|-------------|
| `$getParams`    | **array** |             |
| `$includeEmpty` | **bool**  |             |

***

### getRelativeUrl

Returns the relative url

```php
public getRelativeUrl(bool $includeParams = true): string
```

**Parameters:**

| Parameter        | Type     | Description |
|------------------|----------|-------------|
| `$includeParams` | **bool** |             |

***

### getAbsoluteUrl

Returns the absolute url

```php
public getAbsoluteUrl(bool $includeParams = true): string
```

**Parameters:**

| Parameter        | Type     | Description |
|------------------|----------|-------------|
| `$includeParams` | **bool** |             |

***

### jsonSerialize

Specify data which should be serialized to JSON.

```php
public jsonSerialize(): string
```

**Return Value:**

Data which can be serialized by <b>json_encode</b>,
which is a value of any type other than a resource.

**See Also:**

* http://php.net/manual/en/jsonserializable.jsonserialize.php

***

### __toString

```php
public __toString(): string
```

***
