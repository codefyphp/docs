# Injector

***

* Full name: `\Qubus\Injector\Injector`
* This class implements:
  [`\Qubus\Injector\ServiceContainer`](./ServiceContainer.md)

## Constants

| Constant               | Visibility | Type | Value                 |
|------------------------|------------|------|-----------------------|
| `A_RAW`                | public     |      | ':'                   |
| `A_DELEGATE`           | public     |      | '+'                   |
| `A_DEFINE`             | public     |      | '@'                   |
| `I_BINDINGS`           | public     |      | 1                     |
| `I_DELEGATES`          | public     |      | 2                     |
| `I_PREPARES`           | public     |      | 4                     |
| `I_ALIASES`            | public     |      | 8                     |
| `I_SHARES`             | public     |      | 16                    |
| `I_ALL`                | public     |      | 31                    |
| `STANDARD_ALIASES`     | public     |      | 'standardAliases'     |
| `SHARED_ALIASES`       | public     |      | 'sharedAliases'       |
| `ARGUMENT_DEFINITIONS` | public     |      | 'argumentDefinitions' |
| `ARGUMENT_PROVIDERS`   | public     |      | 'argumentProviders'   |
| `DELEGATIONS`          | public     |      | 'delegations'         |
| `PREPARATIONS`         | public     |      | 'preparations'        |

## Properties

### reflector

```php
protected ?\Qubus\Injector\Reflector $reflector
```

***

### classDefinitions

```php
protected array $classDefinitions
```

***

### paramDefinitions

```php
protected array $paramDefinitions
```

***

### aliases

```php
protected array $aliases
```

***

### shares

```php
protected array $shares
```

***

### prepares

```php
protected array $prepares
```

***

### delegates

```php
protected array $delegates
```

***

### proxies

```php
protected array $proxies
```

***

### preparesProxy

```php
protected array $preparesProxy
```

***

### inProgressMakes

```php
protected array $inProgressMakes
```

***

### argumentDefinitions

```php
protected array $argumentDefinitions
```

***

### config

```php
protected ?\Qubus\Injector\Config\Config $config
```

***

## Methods

### __construct

Instantiate a Injector object.

```php
public __construct(\Qubus\Injector\Config\Config $config, \Qubus\Injector\Reflector|null $reflector = null): mixed
```

**Parameters:**

| Parameter    | Type                                | Description                                                                     |
|--------------|-------------------------------------|---------------------------------------------------------------------------------|
| `$config`    | **\Qubus\Injector\Config\Config**   | Configuration array passed to the Injector.                                     |
| `$reflector` | **\Qubus\Injector\Reflector\|null** | Optional. Reflector class to use for traversal. Falls back to CachingReflector. |

**Throws:**

If the definitions could not be registered.
- [`InvalidMappingsException`](./InvalidMappingsException.md)

***

### __clone

Don't share the instantiation chain across clones.

```php
public __clone(): mixed
```

***

### registerMappings

Register mapping definitions.

```php
public registerMappings(\Qubus\Injector\Config\Config $config): void
```

Takes a Config and reads the following keys to add definitions:
- 'sharedAliases'
- 'standardAliases'
- 'argumentDefinitions'
- 'argumentProviders'
- 'delegations'
- 'preparations'

**Parameters:**

| Parameter | Type                              | Description            |
|-----------|-----------------------------------|------------------------|
| `$config` | **\Qubus\Injector\Config\Config** | Config array to parse. |

**Throws:**

If a needed key could not be read from the config file.
- [`InvalidMappingsException`](./InvalidMappingsException.md)
If the dependency injector could not be set up.
- [`InvalidMappingsException`](./InvalidMappingsException.md)

***

### mapAliases

Map Interfaces to concrete classes for our Injector.

```php
protected mapAliases(string|object $class, string $interface): void
```

**Parameters:**

| Parameter    | Type               | Description                               |
|--------------|--------------------|-------------------------------------------|
| `$class`     | **string\|object** | Concrete implementation to instantiate.   |
| `$interface` | **string**         | Alias to register the implementation for. |

**Throws:**

If the alias could not be created.
- [`ConfigException`](./ConfigException.md)

***

### shareAliases

Tell our Injector which interfaces to share across all requests.

```php
protected shareAliases(string|object $class, string $interface): mixed
```

**Parameters:**

| Parameter    | Type               | Description                               |
|--------------|--------------------|-------------------------------------------|
| `$class`     | **string\|object** | Concrete implementation to instantiate.   |
| `$interface` | **string**         | Alias to register the implementation for. |

**Throws:**

If the interface could not be shared.
- [`ConfigException`](./ConfigException.md)

***

### defineArguments

Tell our Injector how arguments are defined.

```php
protected defineArguments(array $argumentSetup, string $alias): void
```

**Parameters:**

| Parameter        | Type       | Description                                       |
|------------------|------------|---------------------------------------------------|
| `$argumentSetup` | **array**  | Argument providers setup from configuration file. |
| `$alias`         | **string** | The alias for which to define the argument.       |

**Throws:**

If a required config key could not be found.
- [`InvalidMappingsException`](./InvalidMappingsException.md)

***

### defineDelegations

Tell our Injector what instantiations are delegated to factories.

```php
protected defineDelegations(callable $factory, string $alias): void
```

**Parameters:**

| Parameter  | Type         | Description                                       |
|------------|--------------|---------------------------------------------------|
| `$factory` | **callable** | Factory that will take care of the instantiation. |
| `$alias`   | **string**   | The alias for which to define the delegation.     |

**Throws:**

If the delegation could not be configured.
- [`ConfigException`](./ConfigException.md)

***

### definePreparations

Tell our Injector what preparations need to be done.

```php
protected definePreparations(callable $preparation, string $alias): void
```

**Parameters:**

| Parameter      | Type         | Description                                    |
|----------------|--------------|------------------------------------------------|
| `$preparation` | **callable** | Preparation to execute on instantiation.       |
| `$alias`       | **string**   | The alias for which to define the preparation. |

**Throws:**

If a required config key could not be found.
- [`InvalidMappingsException`](./InvalidMappingsException.md)
If the prepare statement was not valid.
- [`InjectionException`](./InjectionException.md)

***

### defineArgumentProviders

Tell our Injector how to produce required arguments.

```php
protected defineArgumentProviders(array $argumentSetup, string $argument): void
```

**Parameters:**

| Parameter        | Type       | Description                                       |
|------------------|------------|---------------------------------------------------|
| `$argumentSetup` | **array**  | Argument providers setup from configuration file. |
| `$argument`      | **string** | The argument to provide.                          |

**Throws:**

If a required config key could not be found.
- [`InvalidMappingsException`](./InvalidMappingsException.md)

***

### addArgumentDefinition

Add a single argument definition.

```php
protected addArgumentDefinition(mixed $callable, string $alias, array $args): void
```

**Parameters:**

| Parameter   | Type       | Description                                                                        |
|-------------|------------|------------------------------------------------------------------------------------|
| `$callable` | **mixed**  | Callable to execute when the argument is needed.                                   |
| `$alias`    | **string** | Alias to add the argument definition to.                                           |
| `$args`     | **array**  | Additional arguments used for definition. Array containing $argument & $interface. |

**Throws:**

If $callable is not a callable.
- [`InvalidMappingsException`](./InvalidMappingsException.md)

***

### getArgumentProxy

Get an argument proxy for a given alias to provide to the injector.

```php
protected getArgumentProxy(string $alias, string $interface, callable $callable): object
```

**Parameters:**

| Parameter    | Type         | Description                            |
|--------------|--------------|----------------------------------------|
| `$alias`     | **string**   | Alias that needs the argument.         |
| `$interface` | **string**   | Interface that the proxy implements.   |
| `$callable`  | **callable** | Callable used to initialize the proxy. |

**Return Value:**

Argument proxy to provide to the inspector.

***

### define

Define instantiation directives for the specified class

```php
public define(string $name, array $args): \Qubus\Injector\ServiceContainer
```

**Parameters:**

| Parameter | Type       | Description                                                        |
|-----------|------------|--------------------------------------------------------------------|
| `$name`   | **string** | The class (or alias) whose constructor arguments we wish to define |
| `$args`   | **array**  | An array mapping parameter names to values/instructions            |

***

### defineParam

Assign a global default value for all parameters named $paramName

```php
public defineParam(string $paramName, mixed $value): \Qubus\Injector\ServiceContainer
```

**Parameters:**

| Parameter    | Type       | Description                                     |
|--------------|------------|-------------------------------------------------|
| `$paramName` | **string** | The parameter name for which this value applies |
| `$value`     | **mixed**  | The value to inject for this parameter name     |

***

### alias

Define an alias for all occurrences of a given typehint

```php
public alias(string $original, string $alias): \Qubus\Injector\ServiceContainer
```

**Parameters:**

| Parameter   | Type       | Description             |
|-------------|------------|-------------------------|
| `$original` | **string** | The typehint to replace |
| `$alias`    | **string** | The implementation name |

***

### normalizeName

```php
private normalizeName(string $className): string
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$className` | **string** |             |

***

### share

Share the specified class/instance across the Injector context

```php
public share(string|object $nameOrInstance): \Qubus\Injector\ServiceContainer
```

**Parameters:**

| Parameter         | Type               | Description                  |
|-------------------|--------------------|------------------------------|
| `$nameOrInstance` | **string\|object** | The class or object to share |

***

### shareClass

```php
private shareClass(string|object $nameOrInstance): void
```

**Parameters:**

| Parameter         | Type               | Description |
|-------------------|--------------------|-------------|
| `$nameOrInstance` | **string\|object** |             |

***

### resolveAlias

```php
private resolveAlias(string $name): array
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### shareInstance

```php
private shareInstance(object $obj): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$obj`    | **object** |             |

***

### prepare

Register a prepare callable to modify/prepare objects of type $name after instantiation

```php
public prepare(string $name, callable|string|array|object $callableOrMethodStr): \Qubus\Injector\ServiceContainer
```

**Parameters:**

| Parameter              | Type                                | Description                                    |
|------------------------|-------------------------------------|------------------------------------------------|
| `$name`                | **string**                          | Class name.                                    |
| `$callableOrMethodStr` | **callable\|string\|array\|object** | Any callable or provisionable invokable method |

***

### isExecutable

```php
private isExecutable(mixed $exe): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$exe`    | **mixed** |             |

***

### delegate

Delegate the creation of $name instances to the specified callable

```php
public delegate(string $name, callable|string|array|object $callableOrMethodStr): \Qubus\Injector\ServiceContainer
```

**Parameters:**

| Parameter              | Type                                | Description                                     |
|------------------------|-------------------------------------|-------------------------------------------------|
| `$name`                | **string**                          | Class name.                                     |
| `$callableOrMethodStr` | **callable\|string\|array\|object** | Any callable or provisionable invokable method. |

***

### inspect

Retrieve stored data for the specified definition type.

```php
public inspect(string|null $nameFilter = null, int|null $typeFilter = null): array
```

Exposes introspection of existing binds/delegates/shares/etc for decoration and composition.

**Parameters:**

| Parameter     | Type             | Description                                   |
|---------------|------------------|-----------------------------------------------|
| `$nameFilter` | **string\|null** | An optional class name filter                 |
| `$typeFilter` | **int\|null**    | A bitmask of Injector::* type constant flags. |

***

### filter

```php
private filter(mixed $source, mixed $name): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$source` | **mixed** |             |
| `$name`   | **mixed** |             |

***

### proxy

Proxy the specified class across the Injector context.

```php
public proxy(string $name, callable|string|array|object $callableOrMethodStr): \Qubus\Injector\ServiceContainer
```

**Parameters:**

| Parameter              | Type                                | Description        |
|------------------------|-------------------------------------|--------------------|
| `$name`                | **string**                          | The class to proxy |
| `$callableOrMethodStr` | **callable\|string\|array\|object** |                    |

***

### make

Instantiate/provision a class instance.

```php
public make(string $name, array $args = []): mixed
```

**Parameters:**

| Parameter | Type       | Description                                      |
|-----------|------------|--------------------------------------------------|
| `$name`   | **string** | Name of an interface/class/alias to instantiate. |
| `$args`   | **array**  | Optional arguments to pass to the object.        |

***

### resolveProxy

```php
private resolveProxy(string $className, string $normalizedClass, array $args): mixed
```

**Parameters:**

| Parameter          | Type       | Description |
|--------------------|------------|-------------|
| `$className`       | **string** |             |
| `$normalizedClass` | **string** |             |
| `$args`            | **array**  |             |

***

### buildWrappedObject

```php
private buildWrappedObject(string $className, string $normalizedClass, array $args): mixed|object
```

**Parameters:**

| Parameter          | Type       | Description |
|--------------------|------------|-------------|
| `$className`       | **string** |             |
| `$normalizedClass` | **string** |             |
| `$args`            | **array**  |             |

***

### provisionInstance

```php
private provisionInstance(string $className, string $normalizedClass, array $definition): mixed
```

**Parameters:**

| Parameter          | Type       | Description |
|--------------------|------------|-------------|
| `$className`       | **string** |             |
| `$normalizedClass` | **string** |             |
| `$definition`      | **array**  |             |

***

### instantiateWithoutConstructorParams

```php
private instantiateWithoutConstructorParams(string $className): mixed
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$className` | **string** |             |

***

### provisionFuncArgs

```php
private provisionFuncArgs(\ReflectionFunctionAbstract $reflFunc, array $definition, ?array $reflParams = null): array
```

**Parameters:**

| Parameter     | Type                            | Description |
|---------------|---------------------------------|-------------|
| `$reflFunc`   | **\ReflectionFunctionAbstract** |             |
| `$definition` | **array**                       |             |
| `$reflParams` | **?array**                      |             |

***

### buildArgFromParamDefineArr

```php
private buildArgFromParamDefineArr(array $definition): mixed
```

**Parameters:**

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `$definition` | **array** |             |

***

### buildArgFromDelegate

```php
private buildArgFromDelegate(string $paramName, mixed $callableOrMethodStr): mixed
```

**Parameters:**

| Parameter              | Type       | Description |
|------------------------|------------|-------------|
| `$paramName`           | **string** |             |
| `$callableOrMethodStr` | **mixed**  |             |

***

### buildArgFromTypeHint

```php
private buildArgFromTypeHint(\ReflectionFunctionAbstract $reflFunc, \ReflectionParameter $reflParam): mixed
```

**Parameters:**

| Parameter    | Type                            | Description |
|--------------|---------------------------------|-------------|
| `$reflFunc`  | **\ReflectionFunctionAbstract** |             |
| `$reflParam` | **\ReflectionParameter**        |             |

***

### buildArgFromReflParam

```php
private buildArgFromReflParam(\ReflectionParameter $reflParam): mixed
```

**Parameters:**

| Parameter    | Type                     | Description |
|--------------|--------------------------|-------------|
| `$reflParam` | **\ReflectionParameter** |             |

***

### prepareInstance

```php
private prepareInstance(object|string $obj, mixed $normalizedClass): mixed
```

**Parameters:**

| Parameter          | Type               | Description |
|--------------------|--------------------|-------------|
| `$obj`             | **object\|string** |             |
| `$normalizedClass` | **mixed**          |             |

***

### execute

Invoke the specified callable or class::method string, provisioning dependencies along the way.

```php
public execute(callable|string|array|object $callableOrMethodStr, array $args = []): mixed
```

**Parameters:**

| Parameter              | Type                                | Description                                                                    |
|------------------------|-------------------------------------|--------------------------------------------------------------------------------|
| `$callableOrMethodStr` | **callable\|string\|array\|object** | A valid PHP callable
or a provisionable ClassName::methodName string.          |
| `$args`                | **array**                           | Optional array specifying params with which to
invoke the provisioned callable |

**Return Value:**

Returns the invocation result returned from calling the generated executable

**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)

***

### buildExecutable

Provision an Executable instance from any valid callable or class::method string

```php
public buildExecutable(callable|string|array|object $callableOrMethodStr): \Qubus\Injector\Executable
```

**Parameters:**

| Parameter              | Type                                | Description                                                           |
|------------------------|-------------------------------------|-----------------------------------------------------------------------|
| `$callableOrMethodStr` | **callable\|string\|array\|object** | A valid PHP callable
or a provisionable ClassName::methodName string. |

**Throws:**

If the Executable structure could not be built.
- [`\Qubus\Injector\InjectionException|\Qubus\Exception\Data\TypeException`](./InjectionException|/Qubus/Exception/Data/TypeException.md)

***

### buildExecutableStruct

```php
private buildExecutableStruct(callable|string|array|object $callableOrMethodStr): array
```

**Parameters:**

| Parameter              | Type                                | Description |
|------------------------|-------------------------------------|-------------|
| `$callableOrMethodStr` | **callable\|string\|array\|object** |             |

***

### buildExecutableStructFromString

```php
private buildExecutableStructFromString(object|string $stringExecutable): array
```

**Parameters:**

| Parameter           | Type               | Description |
|---------------------|--------------------|-------------|
| `$stringExecutable` | **object\|string** |             |

***

### buildStringClassMethodCallable

```php
private buildStringClassMethodCallable(object|string $class, string $method): array
```

**Parameters:**

| Parameter | Type               | Description |
|-----------|--------------------|-------------|
| `$class`  | **object\|string** |             |
| `$method` | **string**         |             |

***

### buildExecutableStructFromArray

```php
private buildExecutableStructFromArray(array $arrayExecutable): array
```

**Parameters:**

| Parameter          | Type      | Description |
|--------------------|-----------|-------------|
| `$arrayExecutable` | **array** |             |

***

### getInjectionChain

Get the chain of instantiations.

```php
public getInjectionChain(): \Qubus\Injector\InjectionChain
```

**Return Value:**

Chain of instantiations.

***

### generateInvalidCallableError

```php
private generateInvalidCallableError(mixed $callableOrMethodStr): mixed
```

**Parameters:**

| Parameter              | Type      | Description |
|------------------------|-----------|-------------|
| `$callableOrMethodStr` | **mixed** |             |

**Throws:**

- [`ConfigException`](./ConfigException.md)

***
