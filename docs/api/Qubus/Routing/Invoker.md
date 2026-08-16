# Invoker

***

* Full name: `\Qubus\Routing\Invoker`
* Parent class: [`Invoker`](../../Invoker/Invoker.md)
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Properties

### requestResolver

```php
protected \Qubus\Routing\TypeHintRequestResolver $requestResolver
```

***

## Methods

### __construct

```php
public __construct(\Psr\Container\ContainerInterface $container): mixed
```

**Parameters:**

| Parameter    | Type                                  | Description |
|--------------|---------------------------------------|-------------|
| `$container` | **\Psr\Container\ContainerInterface** |             |

***

### setRequest

```php
public setRequest(\Psr\Http\Message\ServerRequestInterface $request): self
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

***
