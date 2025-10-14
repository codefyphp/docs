***

# Application





* Full name: `\Codefy\Framework\Application`
* Parent class: [`Container`](../../Qubus/Injector/Psr11/Container.md)
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`APP_VERSION`|public| |&#039;3.0.0-rc.2&#039;|
|`MIN_PHP_VERSION`|public| |&#039;8.4&#039;|
|`DS`|public| |\DIRECTORY_SEPARATOR|

## Properties


### APP

The current globally available Application (if any).

```php
public static ?self $APP
```



* This property is **static**.


***

### charset



```php
public string $charset
```






***

### language



```php
public string $language
```






***

### locale



```php
public string $locale
```






***

### controllerNamespace



```php
public string $controllerNamespace
```






***

### ROOT_PATH



```php
public static string $ROOT_PATH
```



* This property is **static**.


***

### encryptedEnv



```php
public static bool $encryptedEnv
```



* This property is **static**.


***

### basePath



```php
private string $basePath
```






***

### appPath



```php
private ?string $appPath
```






***

### serviceProviders



```php
private array $serviceProviders
```






***

### serviceProvidersRegistered



```php
private array $serviceProvidersRegistered
```






***

### baseMiddlewares



```php
private array $baseMiddlewares
```






***

### booted



```php
public bool $booted
```






***

### hasBeenBootstrapped



```php
private bool $hasBeenBootstrapped
```






***

### bootingCallbacks



```php
private array $bootingCallbacks
```






***

### bootedCallbacks



```php
private array $bootedCallbacks
```






***

### registeredCallbacks



```php
private array $registeredCallbacks
```






***

### param



```php
private array $param
```






***

### request



```php
public \Psr\Http\Message\ServerRequestInterface $request
```






***

### response



```php
public \Psr\Http\Message\ResponseInterface $response
```






***

### assets



```php
public \Codefy\Framework\Support\Assets $assets
```






***

### mailer



```php
public \Qubus\Mail\Mailer $mailer
```






***

### session



```php
public \Qubus\Http\Session\PhpSession $session
```






***

### flash



```php
public \Qubus\Http\Session\Flash $flash
```






***

### event



```php
public \Psr\EventDispatcher\EventDispatcherInterface $event
```






***

### httpCookie



```php
public \Qubus\Http\Cookies\Factory\HttpCookieFactory $httpCookie
```






***

### localStorage



```php
public \Codefy\Framework\Support\LocalStorage $localStorage
```






***

### configContainer



```php
public \Qubus\Config\ConfigContainer $configContainer
```






***

### pipeline



```php
public \Codefy\Framework\Pipeline\PipelineBuilder $pipeline
```






***

### hook



```php
public \Qubus\EventDispatcher\ActionFilter\Observer $hook
```






***

### string



```php
public \Qubus\Support\StringHelper $string
```






***

### array



```php
public \Qubus\Support\ArrayHelper $array
```






***

### router



```php
public \Qubus\Routing\Router $router
```






***

### path



```php
public \Codefy\Framework\Support\Paths $path
```






***

## Methods


### __construct



```php
public __construct(array $params = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$params` | **array** |  |




**Throws:**

- [`ReflectionException`](../../ReflectionException.md)

- [`TypeException`](../../Qubus/Exception/Data/TypeException.md)



***

### registerBaseBindings



```php
private registerBaseBindings(): void
```












***

### inferBasePath

Infer the application's base directory
from the environment and server.

```php
protected static inferBasePath(): string|null
```



* This method is **static**.








***

### getDbConnection



```php
public getDbConnection(): \Qubus\Expressive\Connection
```











**Throws:**

- [`Exception`](../../Qubus/Exception/Exception.md)



***

### getDb



```php
public getDb(): \Qubus\Expressive\QueryBuilder|null
```











**Throws:**

- [`Exception`](../../Qubus/Exception/Exception.md)



***

### version

Return the version of the Application's Framework.

```php
public version(): string
```












***

### singleton

Ensure a value or object will remain globally unique.

```php
public singleton(string $key, callable $value): \Codefy\Framework\Application
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | The value or object name |
| `$value` | **callable** | The closure that defines the object |





***

### registerDefaultServiceProviders



```php
protected registerDefaultServiceProviders(): void
```











**Throws:**

- [`TypeException`](../../Qubus/Exception/Data/TypeException.md)



***

### bootstrapWith



```php
public bootstrapWith(array $bootstrappers): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$bootstrappers` | **array** |  |





***

### getContainer



```php
public getContainer(): \Qubus\Injector\ServiceContainer|\Psr\Container\ContainerInterface
```












***

### setBooted



```php
public setBooted(bool $bool = false): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$bool` | **bool** |  |





***

### boot



```php
public boot(): void
```











**Throws:**

- [`TypeException`](../../Qubus/Exception/Data/TypeException.md)



***

### forceRegisterServiceProvider

Force register a service provider with the application.

```php
public forceRegisterServiceProvider(string|\Qubus\Injector\ServiceProvider\Serviceable|\Qubus\Injector\ServiceProvider\Bootable $provider): \Qubus\Injector\ServiceProvider\Serviceable|\Qubus\Injector\ServiceProvider\Bootable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$provider` | **string&#124;\Qubus\Injector\ServiceProvider\Serviceable&#124;\Qubus\Injector\ServiceProvider\Bootable** |  |




**Throws:**

- [`TypeException`](../../Qubus/Exception/Data/TypeException.md)



***

### registerConfiguredServiceProviders

Register all configured providers.

```php
public registerConfiguredServiceProviders(): void
```











**Throws:**

- [`TypeException`](../../Qubus/Exception/Data/TypeException.md)

- [`Exception`](../../Qubus/Exception/Exception.md)



***

### registerServiceProvider

Register a Service Provider to the application.

```php
public registerServiceProvider(string|\Qubus\Injector\ServiceProvider\Serviceable|\Qubus\Injector\ServiceProvider\Bootable $serviceProvider, bool $force = false): \Qubus\Injector\ServiceProvider\Serviceable|\Qubus\Injector\ServiceProvider\Bootable|string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$serviceProvider` | **string&#124;\Qubus\Injector\ServiceProvider\Serviceable&#124;\Qubus\Injector\ServiceProvider\Bootable** |  |
| `$force` | **bool** |  |




**Throws:**

- [`TypeException`](../../Qubus/Exception/Data/TypeException.md)



***

### getRegisteredServiceProvider

Get the registered service provider instance if it exists.

```php
public getRegisteredServiceProvider(\Qubus\Injector\ServiceProvider\Serviceable|\Qubus\Injector\ServiceProvider\Bootable|string $provider): \Qubus\Injector\ServiceProvider\Serviceable|\Qubus\Injector\ServiceProvider\Bootable|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$provider` | **\Qubus\Injector\ServiceProvider\Serviceable&#124;\Qubus\Injector\ServiceProvider\Bootable&#124;string** |  |





***

### forgetServiceProvider

Forget the ServiceProvider from the application.

```php
public forgetServiceProvider(string|\Qubus\Injector\ServiceProvider\Serviceable|\Qubus\Injector\ServiceProvider\Bootable $serviceProvider): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$serviceProvider` | **string&#124;\Qubus\Injector\ServiceProvider\Serviceable&#124;\Qubus\Injector\ServiceProvider\Bootable** |  |





***

### resolveServiceProvider

Resolve a service provider instance from the class name.

```php
public resolveServiceProvider(string $provider): \Qubus\Injector\ServiceProvider\BaseServiceProvider
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$provider` | **string** |  |





***

### getRegisteredProviders

Get the service providers that have been registered.

```php
public getRegisteredProviders(): array&lt;string,bool&gt;
```












***

### providerIsRegistered

Determine if the given service provider is registered.

```php
public providerIsRegistered(string|\Qubus\Injector\ServiceProvider\Serviceable|\Qubus\Injector\ServiceProvider\Bootable $provider): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$provider` | **string&#124;\Qubus\Injector\ServiceProvider\Serviceable&#124;\Qubus\Injector\ServiceProvider\Bootable** |  |





***

### bootServiceProvider

Boot the given service provider.

```php
protected bootServiceProvider(\Qubus\Injector\ServiceProvider\Serviceable|\Qubus\Injector\ServiceProvider\Bootable $provider): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$provider` | **\Qubus\Injector\ServiceProvider\Serviceable&#124;\Qubus\Injector\ServiceProvider\Bootable** |  |




**Throws:**

- [`TypeException`](../../Qubus/Exception/Data/TypeException.md)



***

### booting

Register a new boot listener.

```php
public booting(callable $callback): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **callable** |  |





***

### booted

Register a new "booted" listener.

```php
public booted(callable $callback): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **callable** |  |





***

### fireAppCallbacks

Call the booting callbacks for the application.

```php
protected fireAppCallbacks(callable[]& $callbacks): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callbacks` | **callable[]** |  |





***

### markServiceProviderAsRegistered

Mark the particular ServiceProvider as having been registered.

```php
protected markServiceProviderAsRegistered(\Qubus\Injector\ServiceProvider\Serviceable|\Qubus\Injector\ServiceProvider\Bootable $serviceProvider): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$serviceProvider` | **\Qubus\Injector\ServiceProvider\Serviceable&#124;\Qubus\Injector\ServiceProvider\Bootable** |  |





***

### hasBeenBootstrapped

Determine if the application has been bootstrapped before.

```php
public hasBeenBootstrapped(): bool
```












***

### withBasePath

Set the Application's base directory.

```php
public withBasePath(string $basePath): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$basePath` | **string** |  |





***

### bindPathsToContainer



```php
protected bindPathsToContainer(): void
```












***

### withAppPath

Set the Application's "app" directory.

```php
public withAppPath(string $appPath): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$appPath` | **string** |  |





***

### path

Get the path to the application's "app" directory.

```php
public path(): string
```












***

### basePath

Get the Application's base directory.

```php
public basePath(): string
```












***

### bootStrapPath

Get the path to the application's "bootstrap" directory.

```php
public bootStrapPath(): string
```












***

### getBootstrapProvidersPath

Get the path to the service provider list in the bootstrap directory.

```php
public getBootstrapProvidersPath(): string
```












***

### configPath

Get the path to the application's "config" directory.

```php
public configPath(): string
```












***

### databasePath

Get the path to the application's "database" directory.

```php
public databasePath(): string
```












***

### localePath

Get the path to the application's "locale" directory.

```php
public localePath(): string
```












***

### publicPath

Get the path to the application's "public" directory.

```php
public publicPath(): string
```












***

### storagePath

Get the path to the application's "storage" directory.

```php
public storagePath(): string
```












***

### resourcePath

Get the path to the application's "resources" directory.

```php
public resourcePath(): string
```












***

### viewPath

Get the path to the application's "view" directory.

```php
public viewPath(): string
```












***

### withLocale



```php
public withLocale(string $locale): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$locale` | **string** |  |





***

### getLocale



```php
public getLocale(): string
```












***

### withControllerNamespace



```php
public withControllerNamespace(string $namespace): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$namespace` | **string** |  |





***

### withBaseMiddlewares



```php
public withBaseMiddlewares(array $middlewares): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$middlewares` | **array** |  |





***

### getBaseMiddlewares



```php
public getBaseMiddlewares(): array
```











**Throws:**

- [`Exception`](../../Qubus/Exception/Exception.md)



***

### isRunningInConsole



```php
public isRunningInConsole(): bool
```












***

### hasDebugModeEnabled

Determine if the application is running with debug mode enabled.

```php
public hasDebugModeEnabled(): bool
```











**Throws:**

- [`Exception`](../../Qubus/Exception/Exception.md)



***

### registered

Register a new callable function.

```php
public registered(callable $callback): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **callable** |  |





***

### coreAliases



```php
protected coreAliases(): array
```












***

### handle



```php
public handle(\Psr\Http\Message\ServerRequestInterface $request): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |




**Throws:**

- [`Exception`](../../Exception.md)



***

### handleRequest



```php
public handleRequest(?\Psr\Http\Message\ServerRequestInterface $request = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **?\Psr\Http\Message\ServerRequestInterface** |  |





***

### loadEnvironment

Load environment file(s).

```php
private static loadEnvironment(string $basePath): void
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$basePath` | **string** |  |




**Throws:**

- [`TypeException`](../../Qubus/Exception/Data/TypeException.md)

- [`ReflectionException`](../../ReflectionException.md)



***

### __get



```php
public __get(mixed $name): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |





***

### __isset



```php
public __isset(mixed $name): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |





***

### __set



```php
public __set(mixed $name, mixed $value): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |
| `$value` | **mixed** |  |





***

### __unset



```php
public __unset(mixed $name): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |





***

### __destruct



```php
public __destruct(): mixed
```












***

### isProduction

Determine if the application is in production.

```php
public isProduction(): bool
```












***

### isDevelopment

Determine if the application is in development.

```php
public isDevelopment(): bool
```












***

### create

Create a new CodefyPHP application instance.

```php
public static create(array $config): \Codefy\Framework\Configuration\ApplicationBuilder
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$config` | **array** |  |




**Throws:**

- [`TypeException`](../../Qubus/Exception/Data/TypeException.md)

- [`ReflectionException`](../../ReflectionException.md)



***

### getInstance

Get the globally available instance of the container.

```php
public static getInstance(?string $path = null): static
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **?string** |  |




**Throws:**

- [`TypeException`](../../Qubus/Exception/Data/TypeException.md)

- [`ReflectionException`](../../ReflectionException.md)



***


## Inherited methods


### getLogger

FileLogger

```php
public static getLogger(): \Psr\Log\LoggerInterface
```



* This method is **static**.







**Throws:**

- [`\ReflectionException|\Qubus\Exception\Data\TypeException`](../../ReflectionException|/Qubus/Exception/Data/TypeException.md)



***

### getSmtpLogger

FileLogger with SMTP support.

```php
public static getSmtpLogger(): \Psr\Log\LoggerInterface
```



* This method is **static**.







**Throws:**

- [`ReflectionException`](../../ReflectionException.md)

- [`TypeException`](../../Qubus/Exception/Data/TypeException.md)



***


***
> Automatically generated on 2025-10-13
