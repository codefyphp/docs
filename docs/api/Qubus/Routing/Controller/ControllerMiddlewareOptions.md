# ControllerMiddlewareOptions

***

* Full name: `\Qubus\Routing\Controller\ControllerMiddlewareOptions`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Properties

### only

```php
protected array $only
```

***

### except

```php
protected array $except
```

***

## Methods

### only

Specify the methods that the middleware applies to

```php
public only(array|string $method): $this
```

**Parameters:**

| Parameter | Type              | Description |
|-----------|-------------------|-------------|
| `$method` | **array\|string** |             |

***

### except

Specify the methods that the middleware does not apply to.

```php
public except(array|string $method): $this
```

**Parameters:**

| Parameter | Type              | Description |
|-----------|-------------------|-------------|
| `$method` | **array\|string** |             |

***

### excludedForMethod

Is a specific method excluded by the options set on this object.

```php
public excludedForMethod(string $method): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$method` | **string** |             |

***
