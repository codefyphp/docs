# InjectorMiddlewareResolver

***

* Full name: `\Qubus\Routing\Route\InjectorMiddlewareResolver`
* This class implements:
  [`\Qubus\Routing\Interfaces\MiddlewareResolver`](../Interfaces/MiddlewareResolver.md)

## Properties

### container

```php
public \Psr\Container\ContainerInterface $container
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

### resolve

Resolves a middleware

```php
public resolve(mixed $definition): \Psr\Http\Server\MiddlewareInterface|callable
```

**Parameters:**

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `$definition` | **mixed** |             |

**Throws:**

- [`ContainerExceptionInterface`](../../../Psr/Container/ContainerExceptionInterface.md)
- [`NotFoundExceptionInterface`](../../../Psr/Container/NotFoundExceptionInterface.md)
- [`TypeException`](../../Exception/Data/TypeException.md)

***

### parseArguments

Parses arguments into 2 different formats:

```php
protected parseArguments(string $argString): array{0: array<int,string>, 1: array<string,string>}
```

- positional: ['manage:users', '/no-access']
- key-value:  ['permission' => 'manage:users', 'redirect' => '/no-access']

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$argString` | **string** |             |

***
