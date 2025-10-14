***

# TypeHintRequestResolver





* Full name: `\Qubus\Routing\TypeHintRequestResolver`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Invoker\ParameterResolver\ParameterResolver`](../../Invoker/ParameterResolver/ParameterResolver.md)
* This class is a **Final class**



## Properties


### request



```php
public \Psr\Http\Message\ServerRequestInterface $request
```






***

## Methods


### getParameters



```php
public getParameters(\ReflectionFunctionAbstract $reflection, array $providedParameters, array $resolvedParameters): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$reflection` | **\ReflectionFunctionAbstract** |  |
| `$providedParameters` | **array** |  |
| `$resolvedParameters` | **array** |  |




**Throws:**

- [`ReflectionException`](../../ReflectionException.md)



***

### createRequestOfType



```php
protected createRequestOfType(\ReflectionClass $requestClass): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$requestClass` | **\ReflectionClass** |  |




**Throws:**

- [`ReflectionException`](../../ReflectionException.md)



***


***
> Automatically generated on 2025-10-13
