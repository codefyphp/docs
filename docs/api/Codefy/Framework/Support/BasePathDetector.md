# BasePathDetector

***

* Full name: `\Codefy\Framework\Support\BasePathDetector`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Properties

### server

```php
private array $server
```

***

### phpSapi

```php
private string $phpSapi
```

***

## Methods

### __construct

The constructor.

```php
public __construct(array|null $server = null, string|null $phpSapi = null): mixed
```

**Parameters:**

| Parameter  | Type             | Description             |
|------------|------------------|-------------------------|
| `$server`  | **array\|null**  | The SERVER data to use. |
| `$phpSapi` | **string\|null** | The PHP_SAPI value.     |

***

### getBasePath

Calculate the url base path.

```php
public getBasePath(): string
```

**Return Value:**

The base path.

***

### getBasePathByScriptName

Return basePath for built-in server.

```php
private getBasePathByScriptName(array $server): string
```

**Parameters:**

| Parameter | Type      | Description             |
|-----------|-----------|-------------------------|
| `$server` | **array** | The SERVER data to use. |

**Return Value:**

The base path.

***

### getBasePathByRequestUri

Return basePath for apache server.

```php
private getBasePathByRequestUri(array $server): string
```

**Parameters:**

| Parameter | Type      | Description             |
|-----------|-----------|-------------------------|
| `$server` | **array** | The SERVER data to use. |

**Return Value:**

The base path.

***
