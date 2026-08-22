---
title: app
sidebar_title: app
summary: Access the CodefyPHP service container or resolve a class, interface, or alias with runtime parameters through the app helper.
keywords: app-helper,dependency-injection,service-container
---


Description
-----------

Returns the `Qubus\Injector\ServiceContainer` or `Psr\Container\ContainerInterface` instance. You may pass a `class`, 
`alias`, or `interface` name to resolve it from the container as well as any needed parameters.

!!!warning
    This helper is available for ease of use, but should be used sparingly. It is highly recommended that you use 
    a [`ServiceProvider`](../../getting-started/dependency-injection.md#service-provider-contracts) or dependency injection.

Usage
-----

```php
<?php

use function Codefy\Framework\Helpers\app;

function app(?string $name = null, array $args = []): mixed;
```

Parameters
----------

**$name** (string|null) (optional) Alias, class, or interface to resolve from the Injector.

**$args** (array) (optional) An array of values that will be used to resolve dependencies.

## Examples

```php
<?php

use function Codefy\Framework\Helpers\app;

return app(); // returns ContainerInterface|ServiceContainer
```

```php
<?php

use Qubus\Routing\Psr7Router;

use function Codefy\Framework\Helpers\app;

$router = app(name: Psr7Router::class); // resolves router from Injector
```

```php
<?php

use Qubus\Routing\Psr7Router;

use function Codefy\Framework\Helpers\app;

$router = app()->alias(
    original: \Psr\SimpleCache\CacheInterface::class,
    alias: \Qubus\Cache\Psr16\SimpleCache::class
); // binds alias to the original (interface)
```
