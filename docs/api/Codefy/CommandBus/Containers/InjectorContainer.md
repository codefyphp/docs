# InjectorContainer

***

* Full name: `\Codefy\CommandBus\Containers\InjectorContainer`
* This class implements:
  [`\Codefy\CommandBus\Container`](../Container.md)

## Properties

### container

```php
public \Qubus\Injector\Psr11\Container $container
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Injector\Psr11\Container $container): mixed
```

**Parameters:**

| Parameter    | Type                                | Description |
|--------------|-------------------------------------|-------------|
| `$container` | **\Qubus\Injector\Psr11\Container** |             |

***

### make

Instantiate and return an object based on its class name.

```php
public make(string $className): mixed
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$className` | **string** |             |

***
