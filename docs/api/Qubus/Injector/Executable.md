***

# Executable





* Full name: `\Qubus\Injector\Executable`



## Properties


### callableReflection



```php
private \ReflectionFunctionAbstract $callableReflection
```






***

### invocationObject



```php
private mixed $invocationObject
```






***

### isInstanceMethod



```php
private bool $isInstanceMethod
```






***

## Methods


### __construct



```php
public __construct(\ReflectionFunctionAbstract $reflFunc, ?object $invocationObject = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$reflFunc` | **\ReflectionFunctionAbstract** |  |
| `$invocationObject` | **?object** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### setMethodCallable



```php
private setMethodCallable(\ReflectionMethod $reflection, ?object $invocationObject): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$reflection` | **\ReflectionMethod** |  |
| `$invocationObject` | **?object** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### __invoke



```php
public __invoke(): mixed
```












***

### invokeClosureCompat



```php
private invokeClosureCompat(mixed $reflection, mixed $args): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$reflection` | **mixed** |  |
| `$args` | **mixed** |  |





***

### getCallableReflection



```php
public getCallableReflection(): \ReflectionFunctionAbstract
```












***

### getInvocationObject



```php
public getInvocationObject(): mixed
```












***

### isInstanceMethod



```php
public isInstanceMethod(): bool
```












***


***
> Automatically generated on 2025-10-13
