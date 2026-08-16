# InjectionException

***

* Full name: `\Qubus\Injector\InjectionException`
* Parent class: [`RuntimeException`](../../RuntimeException.md)
* This class implements:
  [`\Qubus\Injector\InjectorException`](./InjectorException.md)

## Properties

### dependencyChain

```php
public array $dependencyChain
```

***

## Methods

### __construct

```php
public __construct(array $inProgressMakes, mixed $message = "", mixed $code = 0, ?\ReflectionException $previous = null): mixed
```

**Parameters:**

| Parameter          | Type                      | Description |
|--------------------|---------------------------|-------------|
| `$inProgressMakes` | **array**                 |             |
| `$message`         | **mixed**                 |             |
| `$code`            | **mixed**                 |             |
| `$previous`        | **?\ReflectionException** |             |

***

### fromInvalidCallable

Add a human-readable version of the invalid callable to the standard 'invalid invokable' message.

```php
public static fromInvalidCallable(array $inProgressMakes, string|array|object $callableOrMethodStr, ?\ReflectionException $previous = null): mixed
```

* This method is **static**.
**Parameters:**

| Parameter              | Type                      | Description |
|------------------------|---------------------------|-------------|
| `$inProgressMakes`     | **array**                 |             |
| `$callableOrMethodStr` | **string\|array\|object** |             |
| `$previous`            | **?\ReflectionException** |             |

***

### getDependencyChain

Returns the hierarchy of dependencies that were being created when
the exception occurred.

```php
public getDependencyChain(): array
```

***
