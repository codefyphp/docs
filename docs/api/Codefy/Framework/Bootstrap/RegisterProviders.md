***

# RegisterProviders





* Full name: `\Codefy\Framework\Bootstrap\RegisterProviders`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### merge



```php
protected static array $merge
```



* This property is **static**.


***

### bootstrapProviderPath

The path to the bootstrap provider configuration file.

```php
protected static string|null $bootstrapProviderPath
```



* This property is **static**.


***

### providers



```php
public static array $providers
```



* This property is **static**.


***

## Methods


### bootstrap



```php
public bootstrap(\Codefy\Framework\Application $app): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$app` | **\Codefy\Framework\Application** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)

- [`Exception`](../../../Qubus/Exception/Exception.md)



***

### mergeAdditionalProviders

Merge additional configured providers into the configuration.

```php
protected mergeAdditionalProviders(\Codefy\Framework\Application $app): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$app` | **\Codefy\Framework\Application** |  |




**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)



***

### merge

Merge the given providers into the provider configuration
before registration.

```php
public static merge(array $providers, string|null $bootstrapProviderPath = null): void
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$providers` | **array** |  |
| `$bootstrapProviderPath` | **string&#124;null** |  |





***

### flushState



```php
public static flushState(): void
```



* This method is **static**.








***


***
> Automatically generated on 2025-10-13
