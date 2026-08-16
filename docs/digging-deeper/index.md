---
title: Cache
sidebar_title: Cache
weight: 0
---

## Installation

```shell
composer require qubus/cache
```

## Introduction

It is questionable whether cache is necessary or helpful in an event sourced system. Nevertheless, PSR-6 and PSR-16 
cache implementations are available. They currently are utilized only for user and csrf sessions.

The default cache adapter used is `Qubus\Cache\Adapter\FileSystemCacheAdapter`. Predis/Redis, APCu, InMemory, and 
Memcached adapters are also available. If you want to use another adapter, you can switch it out in 
`Application\Provider\Psr16ServiceProvider`.

## Cache Service Provider

Let's say, you wanted to switch out `FileSystemCacheAdapter` for `RedisCacheAdapter`. You would change the service 
provider from this:

```php title="./src/Application/Provider/Psr16ServiceProvider.php"
<?php

declare(strict_types=1);

namespace Application\Provider;

use Codefy\Framework\Support\CodefyServiceProvider;
use Qubus\Exception\Exception;

use function Codefy\Framework\Helpers\storage_path;

class Psr16ServiceProvider extends CodefyServiceProvider
{
    /**
     * @throws Exception
     */
    public function register(): void
    {
        $adapter = new \Qubus\FileSystem\Adapter\LocalFlysystemAdapter(
            config: $this->codefy->make(name: \Qubus\Config\ConfigContainer::class),
            location: storage_path(path: 'framework/cache')
        );
        $filesystem = new \Qubus\FileSystem\FileSystem(adapter: $adapter);
        $cacheAdapter = new \Qubus\Cache\Adapter\FileSystemCacheAdapter(operator: $filesystem);

        $this->codefy->alias(
            original: \Psr\SimpleCache\CacheInterface::class,
            alias: \Qubus\Cache\Psr16\SimpleCache::class
        );

        $this->codefy->define(name: \Qubus\Cache\Psr16\SimpleCache::class, args: [
            ':adapter' => $cacheAdapter,
            ':ttl' => $this->codefy->make(name: 'codefy.config')->getConfigKey(key: 'cache.ttl'),
            ':namespace' => $this->codefy->make(name: 'codefy.config')->getConfigKey(key: 'cache.namespace'),
        ]);

        $this->codefy->share(nameOrInstance: \Psr\SimpleCache\CacheInterface::class);
    }
}
```

to this instead:

```php title="./src/Application/Provider/Psr16ServiceProvider.php"
<?php

declare(strict_types=1);

namespace Application\Provider;

use Codefy\Framework\Support\CodefyServiceProvider;
use Qubus\Cache\Adapter\RedisCacheAdapter;
use Qubus\Exception\Exception;
use Redis;

class Psr16ServiceProvider extends CodefyServiceProvider
{
    /**
     * @throws Exception
     */
    public function register(): void
    {
        $cacheAdapter = new RedisCacheAdapter(new Redis([
            'host' => $this->codefy->configContainer->getConfigKey(key: 'cache.redis.host'),
            'port' => $this->codefy->configContainer->getConfigKey(key: 'cache.redis.port'),
            'persistent' => $this->codefy->configContainer->getConfigKey(key: 'cache.redis.persistent'),
        ]));

        $this->codefy->alias(
            original: \Psr\SimpleCache\CacheInterface::class,
            alias: \Qubus\Cache\Psr16\SimpleCache::class
        );

        $this->codefy->define(name: \Qubus\Cache\Psr16\SimpleCache::class, args: [
            ':adapter' => $cacheAdapter,
            ':ttl' => $this->codefy->make(name: 'codefy.config')->getConfigKey(key: 'cache.ttl'),
            ':namespace' => $this->codefy->make(name: 'codefy.config')->getConfigKey(key: 'cache.namespace'),
        ]);

        $this->codefy->share(nameOrInstance: \Psr\SimpleCache\CacheInterface::class);
    }
}
```

If `cache.redis.persistent` is set to `true`, cache files will be saved in `./storage` instead of in 
`./storage/framework/cache` because `./storage` is the default setting of where files are saved if it is not explicitly 
defined.

## Cache Middlewares

There are cache middlewares available to cache different aspects of your application:

* `Codefy\Framework\Http\Middleware\ContentCacheMiddleware::class`
    * __Alias:__ `content.cache`
    * __Description:__ Caching of almost any content produced in a PHP execution loop like `PHP`, `HTML`, etc.
* `Codefy\Framework\Http\Middleware\Cache\CacheMiddleware::class`
    * __Alias:__ `http.cache`
    * __Description:__ Saves the response headers in a PSR-6 cache pool and returns `304` responses (Not modified) if the response is still valid (based on its `ETag` or `Last-Modified` header). It's recommended to combine it with `http.cache.expires` to set the lifetime of the responses.
* `Codefy\Framework\Http\Middleware\Cache\ClearSiteDataMiddleware::class`
    * __Alias:__ `http.cache.clear.data`
    * __Description:__ Send the header `Clear-Site-Data` to remove all site data in the client (`cache`, `cookies`, `storage`, etc.).
* `Codefy\Framework\Http\Middleware\Cache\CacheExpiresMiddleware::class`
    * __Alias:__ `http.cache.expires`
    * __Description:__ This middleware adds the `Expires` and `Cache-Control: max-age` headers to the response. You can configure the cache duration for each mimetype (`File: ./config/http-cache.php`).
* `Codefy\Framework\Http\Middleware\Cache\CachePreventionMiddleware::class`
    * __Alias:__ `http.cache.prevention`
    * __Description:__ To add the response headers for cache prevention. Useful in development environments.

!!! warning "Note"
    To use any of these middlewares, uncomment them in `./config/app.php`, and then add them to your routes, controllers, 
    or to the `base_middlewares` array.

