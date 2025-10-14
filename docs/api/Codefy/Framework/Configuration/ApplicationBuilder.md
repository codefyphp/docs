***

# ApplicationBuilder





* Full name: `\Codefy\Framework\Configuration\ApplicationBuilder`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### app



```php
protected \Codefy\Framework\Application $app
```






***

## Methods


### __construct



```php
public __construct(\Codefy\Framework\Application $app): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$app` | **\Codefy\Framework\Application** |  |





***

### withKernels

Register the kernels for the application.

```php
public withKernels(): $this
```












***

### withProviders

Register additional service providers.

```php
public withProviders(array $providers = [], bool $withBootstrapProviders = true): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$providers` | **array** |  |
| `$withBootstrapProviders` | **bool** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### withSingletons

Register an array of singletons that are resource intensive
or are not called often.

```php
public withSingletons(array $singletons = []): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$singletons` | **array** |  |





***

### withRouting

Register the routing services for the application.

```php
public withRouting(callable|\Closure|null $using = null, array|string|null $web = null, array|null $class = null, array|string|null $api = null, string $apiPrefix = &#039;api&#039;, callable|null $then = null): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$using` | **callable&#124;\Closure&#124;null** |  |
| `$web` | **array&#124;string&#124;null** |  |
| `$class` | **array&#124;null** |  |
| `$api` | **array&#124;string&#124;null** |  |
| `$apiPrefix` | **string** |  |
| `$then` | **callable&#124;null** |  |




**Throws:**

- [`TypeException`](../../../Qubus/Exception/Data/TypeException.md)



***

### withEncryptedEnv

Set whether environment variables
should be encrypted.

```php
public withEncryptedEnv(bool $bool = false): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$bool` | **bool** | Default: false. |





***

### buildRoutingCallback

Create the routing callback for the application.

```php
protected buildRoutingCallback(array|string|null $web = null, array|string|null $api = null, string $apiPrefix = &#039;api&#039;, callable|null $then = null): \Closure
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$web` | **array&#124;string&#124;null** |  |
| `$api` | **array&#124;string&#124;null** |  |
| `$apiPrefix` | **string** |  |
| `$then` | **callable&#124;null** |  |





***

### registered

Register a callback to be invoked when the application's
service providers are registered.

```php
public registered(callable $callback): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **callable** |  |





***

### booting

Register a callback to be invoked when the application is "booting".

```php
public booting(callable $callback): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **callable** |  |





***

### booted

Register a callback to be invoked when the application is "booted".

```php
public booted(callable $callback): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **callable** |  |





***

### return

Return the application instance.

```php
public return(): \Codefy\Framework\Application
```












***


***
> Automatically generated on 2025-10-13
