# BaseServiceProvider

***

* Full name: `\Qubus\Injector\ServiceProvider\BaseServiceProvider`
* This class implements:
  [`\Qubus\Injector\ServiceProvider\Serviceable`](./Serviceable.md),
  [`\Qubus\Injector\ServiceProvider\Bootable`](./Bootable.md)
* This class is an **Abstract class**

## Properties

### container

```php
protected \Qubus\Injector\ServiceContainer $container
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Injector\ServiceContainer $container): mixed
```

**Parameters:**

| Parameter    | Type                                 | Description |
|--------------|--------------------------------------|-------------|
| `$container` | **\Qubus\Injector\ServiceContainer** |             |

***

### register

Register services that need to be loaded during
the booting stage.

```php
public register(): void
```

***

### boot

Other services, extensions, callbacks, etc. that need
to be loaded after the called provider is booted.

```php
public boot(): void
```

***
