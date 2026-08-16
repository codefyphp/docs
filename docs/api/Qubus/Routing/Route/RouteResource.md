# RouteResource

***

* Full name: `\Qubus\Routing\Route\RouteResource`

## Properties

### methodActionDefaults

The default actions/methods for a resourceful controller.

```php
protected array $methodActionDefaults
```

***

### methodActionNames

```php
protected static array $methodActionNames
```

* This property is **static**.

***

### parameters

The parameters set for this resource instance.

```php
protected string|array $parameters
```

***

### parameterMap

The global parameter mapping.

```php
protected static array $parameterMap
```

* This property is **static**.

***

### router

```php
public \Qubus\Routing\Interfaces\Mappable|\Qubus\Routing\Interfaces\Routable $router
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Routing\Interfaces\Mappable|\Qubus\Routing\Interfaces\Routable $router): mixed
```

**Parameters:**

| Parameter | Type                                                                       | Description |
|-----------|----------------------------------------------------------------------------|-------------|
| `$router` | **\Qubus\Routing\Interfaces\Mappable\|\Qubus\Routing\Interfaces\Routable** |             |

***

### register

Route a resource to a controller.

```php
public register(string $name, string $controller, array $options = []): mixed
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$name`       | **string** |             |
| `$controller` | **string** |             |
| `$options`    | **array**  |             |

***

### prefixedResource

Build a set of prefixed resource routes.

```php
protected prefixedResource(string $name, string $controller, array $options): mixed
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$name`       | **string** |             |
| `$controller` | **string** |             |
| `$options`    | **array**  |             |

***

### getResourcePrefix

Extract the resource and prefix from a resource name.

```php
protected getResourcePrefix(string $name): array
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### getResourceMethods

Get the applicable resource methods.

```php
protected getResourceMethods(array $defaults, array $options): array
```

**Parameters:**

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `$defaults` | **array** |             |
| `$options`  | **array** |             |

***

### getResourceUri

Get the base resource URI for a given resource.

```php
public getResourceUri(string $resource): string
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$resource` | **string** |             |

***

### getNestedResourceUri

Get the URI for a nested resource segment array.

```php
protected getNestedResourceUri(array $segments): string
```

**Parameters:**

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `$segments` | **array** |             |

***

### getResourceParameter

Format a resource parameter for usage.

```php
public getResourceParameter(string $value): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$value`  | **string** |             |

***

### getResourceAction

Get the action array for a resource route.

```php
protected getResourceAction(string $resource, string $controller, string $method, array $options): array
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$resource`   | **string** |             |
| `$controller` | **string** |             |
| `$method`     | **string** |             |
| `$options`    | **array**  |             |

***

### getResourceRouteName

Get the name for a given resource.

```php
protected getResourceRouteName(string $resource, string $method, array $options): string
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$resource` | **string** |             |
| `$method`   | **string** |             |
| `$options`  | **array**  |             |

***

### addResourceIndex

Add the index method for a resourceful route.

```php
protected addResourceIndex(string $name, string $base, string $controller, array $options): mixed
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$name`       | **string** |             |
| `$base`       | **string** |             |
| `$controller` | **string** |             |
| `$options`    | **array**  |             |

***

### addResourceCreate

Add the create method for a resourceful route.

```php
protected addResourceCreate(string $name, string $base, string $controller, array $options): mixed
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$name`       | **string** |             |
| `$base`       | **string** |             |
| `$controller` | **string** |             |
| `$options`    | **array**  |             |

***

### addResourceStore

Add the store method for a resourceful route.

```php
protected addResourceStore(string $name, string $base, string $controller, array $options): mixed
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$name`       | **string** |             |
| `$base`       | **string** |             |
| `$controller` | **string** |             |
| `$options`    | **array**  |             |

***

### addResourceShow

Add the show method for a resourceful route.

```php
protected addResourceShow(string $name, string $base, string $controller, array $options): mixed
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$name`       | **string** |             |
| `$base`       | **string** |             |
| `$controller` | **string** |             |
| `$options`    | **array**  |             |

***

### addResourceEdit

Add the edit method for a resourceful route.

```php
protected addResourceEdit(string $name, string $base, string $controller, array $options): mixed
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$name`       | **string** |             |
| `$base`       | **string** |             |
| `$controller` | **string** |             |
| `$options`    | **array**  |             |

***

### addResourceUpdate

Add the update method for a resourceful route.

```php
protected addResourceUpdate(string $name, string $base, string $controller, array $options): mixed
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$name`       | **string** |             |
| `$base`       | **string** |             |
| `$controller` | **string** |             |
| `$options`    | **array**  |             |

***

### addResourceDestroy

Add the destroy method for a resourceful route.

```php
protected addResourceDestroy(string $name, string $base, string $controller, array $options): mixed
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$name`       | **string** |             |
| `$base`       | **string** |             |
| `$controller` | **string** |             |
| `$options`    | **array**  |             |

***

### getShallowName

Get the name for a given resource with shallowness applied when applicable.

```php
protected getShallowName(string $name, array $options): string
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$name`    | **string** |             |
| `$options` | **array**  |             |

***

### getParameters

Get the global parameter map.

```php
public static getParameters(): array
```

* This method is **static**.
***

### setParameters

Set the global parameter mapping.

```php
public static setParameters(array $parameters = []): void
```

* This method is **static**.
**Parameters:**

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `$parameters` | **array** |             |

***

### setMethodActionNames

Define custom method/action name for resource controller.

```php
public static setMethodActionNames(array $names): void
```

* This method is **static**.
**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$names`  | **array** |             |

***

### getMethodActionNames

Get method/action names.

```php
public getMethodActionNames(): array
```

***

### methodActionNames

Get or set the action verbs used in the resource URIs.

```php
public static methodActionNames(array $methodActionNames = []): array
```

* This method is **static**.
**Parameters:**

| Parameter            | Type      | Description |
|----------------------|-----------|-------------|
| `$methodActionNames` | **array** |             |

***
