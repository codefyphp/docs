***

# ServiceContainer





* Full name: `\Qubus\Injector\ServiceContainer`



## Methods


### define

Define instantiation directives for the specified class

```php
public define(string $name, array $args): \Qubus\Injector\ServiceContainer
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | The class (or alias) whose constructor arguments we wish to define |
| `$args` | **array** | An array mapping parameter names to values/instructions |





***

### defineParam

Assign a global default value for all parameters named $paramName

```php
public defineParam(string $paramName, mixed $value): \Qubus\Injector\ServiceContainer
```

Global parameter definitions are only used for parameters with no typehint, pre-defined or
call-time definition.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$paramName` | **string** | The parameter name for which this value applies |
| `$value` | **mixed** | The value to inject for this parameter name |





***

### alias

Define an alias for all occurrences of a given typehint

```php
public alias(string $original, string $alias): \Qubus\Injector\ServiceContainer
```

Use this method to specify implementation classes for interface and abstract class typehints.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$original` | **string** | The typehint to replace |
| `$alias` | **string** | The implementation name |




**Throws:**
<p>If any argument is empty or not a string.</p>

- [`ConfigException`](./ConfigException.md)



***

### share

Share the specified class/instance across the Injector context

```php
public share(mixed $nameOrInstance): \Qubus\Injector\ServiceContainer
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$nameOrInstance` | **mixed** | The class or object to share |




**Throws:**
<p>If $nameOrInstance is not a string or an object.</p>

- [`ConfigException`](./ConfigException.md)



***

### prepare

Register a prepare callable to modify/prepare objects of type $name after instantiation

```php
public prepare(string $name, callable|string|array|object $callableOrMethodStr): \Qubus\Injector\ServiceContainer
```

Any callable or provisionable invokable may be specified. Preparers are passed two
arguments: the instantiated object to be mutated and the current Injector instance.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | Class name. |
| `$callableOrMethodStr` | **callable&#124;string&#124;array&#124;object** | Any callable or provisionable invokable method |




**Throws:**
<p>If $callableOrMethodStr is not a callable.
See https://docs.stalframework.com/injector/#injecting-for-execution.</p>

- [`InjectionException`](./InjectionException.md)



***

### delegate

Delegate the creation of $name instances to the specified callable

```php
public delegate(string $name, callable|string|array|object $callableOrMethodStr): \Qubus\Injector\ServiceContainer
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | Class name. |
| `$callableOrMethodStr` | **callable&#124;string&#124;array&#124;object** | Any callable or provisionable invokable method. |




**Throws:**
<p>If $callableOrMethodStr is not a callable.</p>

- [`ConfigException`](./ConfigException.md)



***

### proxy

Proxy the specified class across the Injector context.

```php
public proxy(string $name, callable|string|array|object $callableOrMethodStr): \Qubus\Injector\ServiceContainer
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | The class to proxy |
| `$callableOrMethodStr` | **callable&#124;string&#124;array&#124;object** |  |




**Throws:**

- [`ConfigException`](./ConfigException.md)



***

### make

Instantiate/provision a class instance.

```php
public make(string $name, array $args = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | Name of an interface/class/alias to instantiate. |
| `$args` | **array** | Optional arguments to pass to the object. |




**Throws:**
<p>If a cyclic gets detected when provisioning.</p>

- [`InjectionException`](./InjectionException.md)



***

### execute

Invoke the specified callable or class::method string, provisioning dependencies along the way.

```php
public execute(callable|string|array|object $callableOrMethodStr, array $args = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callableOrMethodStr` | **callable&#124;string&#124;array&#124;object** | A valid PHP callable<br />or a provisionable ClassName::methodName string. |
| `$args` | **array** | Optional array specifying params with which to<br />invoke the provisioned callable |


**Return Value:**

Returns the invocation result returned from calling the generated executable



**Throws:**

- [`InjectionException`](./InjectionException.md)



***


***
> Automatically generated on 2025-10-13
