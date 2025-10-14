***

# Reflector





* Full name: `\Qubus\Injector\Reflector`



## Methods


### getClass

Retrieves ReflectionClass instances, caching them for future retrieval.

```php
public getClass(string|object $class): \ReflectionClass
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$class` | **string&#124;object** | Class name to retrieve the ReflectionClass from. |


**Return Value:**

ReflectionClass object for the specified class.




***

### getConstructor

Retrieves and caches the constructor (ReflectionMethod) for the specified class.

```php
public getConstructor(string|object $class): \ReflectionMethod|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$class` | **string&#124;object** | Class name to retrieve the constructor from. |


**Return Value:**

ReflectionMethod for the constructor of the specified class.




***

### getConstructorParams

Retrieves and caches an array of constructor parameters for the given class

```php
public getConstructorParams(string|object $class): \ReflectionParameter[]|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$class` | **string&#124;object** | Class name to retrieve the constructor arguments from. |


**Return Value:**

Array of ReflectionParameter objects for the given class' constructor.




***

### getParamTypeHint

Retrieves the class type-hint from a given ReflectionParameter.

```php
public getParamTypeHint(\ReflectionFunctionAbstract $function, \ReflectionParameter $param): string|null
```

There is no way to directly access a parameter's type-hint without
instantiating a new ReflectionClass instance and calling its getName()
method. This method stores the results of this approach so that if
the same parameter type-hint or ReflectionClass is needed again we
already have it cached.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$function` | **\ReflectionFunctionAbstract** | Reflection object for the function. |
| `$param` | **\ReflectionParameter** | Reflection object for the parameter. |


**Return Value:**

Type-hint of the class. Null if none available.




***

### getFunction

Retrieves and caches a reflection for the specified function

```php
public getFunction(string|\Closure $functionName): \ReflectionFunction
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$functionName` | **string&#124;\Closure** | Name of the function to get a reflection for. |


**Return Value:**

ReflectionFunction object for the specified function.




***

### getMethod

Retrieves and caches a reflection for the specified class method

```php
public getMethod(string|object $classNameOrInstance, string $methodName): \ReflectionMethod
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$classNameOrInstance` | **string&#124;object** | Class name or instance the method is referring to. |
| `$methodName` | **string** | Name of the method to get the reflection for. |


**Return Value:**

ReflectionMethod object for the specified method.




***


***
> Automatically generated on 2025-10-13
