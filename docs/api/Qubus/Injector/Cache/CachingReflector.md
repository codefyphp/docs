***

# CachingReflector





* Full name: `\Qubus\Injector\Cache\CachingReflector`
* This class implements:
[`\Qubus\Injector\Reflector`](../Reflector.md)


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`CACHE_KEY_CLASSES`|public| |&#039;injector.refls.classes.&#039;|
|`CACHE_KEY_CTORS`|public| |&#039;injector.refls.ctors.&#039;|
|`CACHE_KEY_CTOR_PARAMS`|public| |&#039;injector.refls.ctor-params.&#039;|
|`CACHE_KEY_FUNCS`|public| |&#039;injector.refls.funcs.&#039;|
|`CACHE_KEY_METHODS`|public| |&#039;injector.refls.methods.&#039;|

## Properties


### reflector



```php
private ?\Qubus\Injector\Reflector $reflector
```






***

### cache



```php
private ?\Qubus\Injector\Cache\ReflectionCache $cache
```






***

## Methods


### __construct



```php
public __construct(?\Qubus\Injector\Reflector $reflector = null, ?\Qubus\Injector\Cache\ReflectionCache $cache = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$reflector` | **?\Qubus\Injector\Reflector** |  |
| `$cache` | **?\Qubus\Injector\Cache\ReflectionCache** |  |





***

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
