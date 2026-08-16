# RouteAction

***

* Full name: `\Qubus\Routing\Route\RouteAction`

## Properties

### callable

```php
protected mixed $callable
```

***

### controller

```php
protected mixed $controller
```

***

### invoker

```php
protected ?\Qubus\Routing\Invoker $invoker
```

***

### controllerName

```php
protected ?string $controllerName
```

***

### controllerMethod

```php
protected ?string $controllerMethod
```

***

### namespace

```php
protected ?string $namespace
```

***

## Methods

### __construct

Constructor

```php
public __construct(mixed $action, ?string $namespace = null, ?\Qubus\Routing\Invoker $invoker = null): mixed
```

Actions created with a Controller string (e.g. `MyController@myMethod`) are lazy loaded
and the Controller class will only be instantiated when required.

**Parameters:**

| Parameter    | Type                        | Description |
|--------------|-----------------------------|-------------|
| `$action`    | **mixed**                   |             |
| `$namespace` | **?string**                 |             |
| `$invoker`   | **?\Qubus\Routing\Invoker** |             |

***

### invoke

Invoke the action.

```php
public invoke(\Psr\Http\Message\ServerRequestInterface $request, \Qubus\Routing\Route\RouteParams $params): mixed
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |
| `$params`  | **\Qubus\Routing\Route\RouteParams**         |             |

***

### createCallableFromAction

If the action is a Controller string, a factory callable is
returned to allow for lazy loading.

```php
private createCallableFromAction(mixed $action): callable
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$action` | **mixed** |             |

***

### isControllerAction

Is this a known Controller based action?

```php
private isControllerAction(): bool
```

***

### getController

Get the Controller for this action. The Controller will only be created once.

```php
private getController(): string|object|null
```

**Return Value:**

Returns null if this is not a Controller based action.

***

### createControllerFromClassName

Instantiate a Controller object from the provided class name.

```php
private createControllerFromClassName(string $className): mixed
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$className` | **string** |             |

***

### providesMiddleware

Can this action provide Middleware.

```php
private providesMiddleware(): bool
```

***

### getMiddlewares

Get an array of Middleware.

```php
public getMiddlewares(): array
```

***

### convertClassStringToFactory

Create a factory Closure for the given Controller string.

```php
private convertClassStringToFactory(string $string): \Closure
```

**Parameters:**

| Parameter | Type       | Description                  |
|-----------|------------|------------------------------|
| `$string` | **string** | e.g. `MyController@myMethod` |

**Throws:**

- [`RouteParseException`](../Exceptions/RouteParseException.md)
- [`RouteControllerNotFoundException`](../Exceptions/RouteControllerNotFoundException.md)
- [`RouteMethodNotFoundException`](../Exceptions/RouteMethodNotFoundException.md)

***

### getActionName

Get the human-readable name of this action.

```php
public getActionName(): string
```

***

### resolveController

```php
private resolveController(callable|object|string|string[] $controller): callable|object|string|string[]
```

**Parameters:**

| Parameter     | Type                                   | Description |
|---------------|----------------------------------------|-------------|
| `$controller` | **callable\|object\|string\|string[]** |             |

***
