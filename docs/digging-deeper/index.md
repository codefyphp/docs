---
title: Cache
sidebar_title: Cache
weight: 0
---

## Requirements

- PHP 8.4 or later
- The PHP extension required by the selected native backend: `apcu`, `redis`, or `memcached`

## Installation

```shell
composer require qubus/cache
```

## Introduction

Qubus Cache provides PSR-16 simple caching and PSR-6 cache pools over in-memory, filesystem, APCu, Redis, Predis,
and Memcached backends.

All examples assume Composer's autoloader has been loaded:

```php
<?php

declare(strict_types=1);

require __DIR__ . '/vendor/autoload.php';
```

## Choosing an API

The facade classes implement both interfaces:

- `Psr\SimpleCache\CacheInterface` (PSR-16): direct key/value operations.
- `Psr\Cache\CacheItemPoolInterface` (PSR-6): cache-item objects, absolute expiration, and deferred writes.

```php
use Psr\Cache\CacheItemPoolInterface;
use Psr\SimpleCache\CacheInterface;
use Qubus\Cache\InMemoryCache;

$cache = new InMemoryCache(ttl: 300, namespace: 'application');

assert($cache instanceof CacheInterface);
assert($cache instanceof CacheItemPoolInterface);
```

PSR-16 and PSR-6 use separate internal prefixes. A value written with `set()` is therefore not returned by `getItem()`, and a value saved with `save()` is not returned by `get()`. Calling `clear()` on a facade clears both API prefixes for its namespace.

## Creating a cache

Each facade accepts an optional default TTL and namespace:

```php
$cache = new InMemoryCache(
    ttl: 300,              // integer seconds, DateInterval, or null
    namespace: 'products', // isolates this cache from other consumers
);
```

### In-memory

Use the in-memory cache for request-local caching and tests. Data belongs to that cache instance and is not shared with another PHP process or another `InMemoryCache` instance.

```php
use Qubus\Cache\InMemoryCache;

$cache = new InMemoryCache(ttl: 60, namespace: 'request');
$cache->set('current-user', ['id' => 42]);
```

### Filesystem

`FileSystemCache` accepts any Flysystem `FilesystemOperator`.

```php
use League\Flysystem\Filesystem;
use League\Flysystem\Local\LocalFilesystemAdapter;
use Qubus\Cache\FileSystemCache;

$local = new LocalFilesystemAdapter(__DIR__ . '/var/cache');
$filesystem = new Filesystem($local);

$cache = new FileSystemCache(
    operator: $filesystem,
    ttl: 3600,
    namespace: 'application',
);

$cache->set('configuration', ['debug' => false]);
```

The cache directory must be readable and writable by the PHP process. Cache values are serialized, so the directory must be treated as trusted application storage.

Expired and malformed files are removed when accessed. Use `prune()` to delete expired files that are never accessed again:

```php
if (! $cache->prune()) {
    throw new RuntimeException('Some cache files could not be inspected or removed.');
}
```

Run `prune()` periodically for persistent filesystem caches, for example from a cron job or scheduled worker. Unrelated files within the Flysystem root are preserved.

### Redis

```php
use Qubus\Cache\RedisCache;

$redis = new \Redis();
$redis->connect('127.0.0.1', 6379, 2.0);
$redis->select(1);
$redis->setOption(\Redis::OPT_SERIALIZER, \Redis::SERIALIZER_PHP);

$cache = new RedisCache(
    redis: $redis,
    ttl: 600,
    namespace: 'application',
);

$cache->set('health', 'ok');
```

Configure Redis authentication and TLS on the client before constructing the cache when required. Enable a Redis serializer when caching arrays or objects. Any `Redis::OPT_PREFIX` value is respected.

### Predis

Predis is exposed through its adapter. Wrap the adapter in `SimpleCache`, `ItemPool`, or both.

```php
use Predis\Client;
use Qubus\Cache\Adapter\PredisCacheAdapter;
use Qubus\Cache\Psr16\SimpleCache;
use Qubus\Cache\Psr6\ItemPool;

$client = new Client([
    'scheme' => 'tcp',
    'host' => '127.0.0.1',
    'port' => 6379,
    'database' => 1,
]);

$adapter = new PredisCacheAdapter($client);

$simpleCache = new SimpleCache($adapter, ttl: 600, namespace: 'application');
$itemPool = new ItemPool($adapter, ttl: 600, namespace: 'application');

$simpleCache->set('health', 'ok');

$item = $itemPool->getItem('report');
$itemPool->save($item->set(['status' => 'ready'])->expiresAfter(600));
```

Clearing a `SimpleCache` or `ItemPool` created this way removes only entries matching that API and namespace. Calling `PredisCacheAdapter::purge(null)` directly flushes the selected Redis database and should be reserved for administrative use.

### Memcached

```php
use Qubus\Cache\MemcachedCache;

$memcached = new \Memcached();
$memcached->addServer('127.0.0.1', 11211);

$cache = new MemcachedCache(
    memcached: $memcached,
    ttl: 600,
    namespace: 'application',
);

$cache->set('health', 'ok');
```

Configure serializers, authentication, persistent IDs, and server pools on the `Memcached` client before passing it to the cache.

### APCu

```php
use Qubus\Cache\ApcuCache;

if (! extension_loaded('apcu')) {
    throw new RuntimeException('The APCu extension is required.');
}

$cache = new ApcuCache(ttl: 300, namespace: 'application');
$cache->set('health', 'ok');
```

APCu is local to a PHP host and SAPI. For command-line use, APCu normally requires `apc.enable_cli=1`.

## PSR-16 usage

### Read, write, inspect, and delete

```php
use Qubus\Cache\InMemoryCache;

$cache = new InMemoryCache(ttl: 300, namespace: 'catalog');

if (! $cache->set('product.42', ['name' => 'Keyboard', 'price' => 99.00])) {
    throw new RuntimeException('The value could not be cached.');
}

$product = $cache->get('product.42', default: null);
$exists = $cache->has('product.42');

if (! $cache->delete('product.42')) {
    throw new RuntimeException('The value could not be deleted.');
}
```

`null` is a valid cached value. Use `has()` when application logic must distinguish a cached `null` from a missing key.

### Expiration

```php
use DateInterval;
use Qubus\Cache\InMemoryCache;

$cache = new InMemoryCache(ttl: 300);

$cache->set('uses-default', 'value');                // 300 seconds
$cache->set('one-minute', 'value', 60);              // 60 seconds
$cache->set('interval', 'value', new DateInterval('PT15M'));
$cache->set('remove-now', 'value', 0);               // immediately removed
$cache->set('remove-now-too', 'value', -1);          // immediately removed
```

Passing `null` to `set()` uses the constructor's default TTL. When both values are `null`, the adapter stores the entry without a finite TTL. Inverted `DateInterval` values resolve to a non-positive TTL and remove the entry.

### Multiple values and iterables

```php
$cache->setMultiple([
    'product.1' => ['name' => 'Mouse'],
    'product.2' => ['name' => 'Keyboard'],
], ttl: 600);

$products = $cache->getMultiple(
    ['product.1', 'product.2', 'product.3'],
    default: ['name' => 'Unknown'],
);

$cache->deleteMultiple(['product.1', 'product.2']);
```

Generators are accepted:

```php
$values = (static function (): iterable {
    yield 'first' => 1;
    yield 'second' => 2;
})();

$cache->setMultiple($values, ttl: 60);
```

### Clear a namespace

```php
if (! $cache->clear()) {
    throw new RuntimeException('The cache could not be cleared.');
}
```

On a facade such as `InMemoryCache` or `FileSystemCache`, `clear()` removes both PSR-16 and PSR-6 entries belonging to its namespace. It does not intentionally clear other namespaces.

## PSR-6 usage

### Read and save an item

```php
use Qubus\Cache\InMemoryCache;

$pool = new InMemoryCache(ttl: 300, namespace: 'users');
$item = $pool->getItem('user.42');

if (! $item->isHit()) {
    $user = ['id' => 42, 'name' => 'Ada'];
    $item->set($user)->expiresAfter(300);

    if (! $pool->save($item)) {
        throw new RuntimeException('The cache item could not be saved.');
    }
}

$user = $item->get();
```

Items must be obtained from the pool that saves them. Passing an arbitrary `CacheItemInterface` implementation is rejected with `Qubus\Cache\TypeException`.

### Absolute and interval expiration

```php
use DateInterval;
use DateTimeImmutable;

$absolute = $pool->getItem('absolute');
$absolute->set('value')->expiresAt(new DateTimeImmutable('+1 hour'));
$pool->save($absolute);

$relative = $pool->getItem('relative');
$relative->set('value')->expiresAfter(new DateInterval('PT15M'));
$pool->save($relative);

$default = $pool->getItem('default');
$default->set('value');
$pool->save($default);
```

`expiresAfter(null)` and `expiresAt(null)` represent no practical expiration using the library's long-lived default horizon.

### Read and delete multiple items

```php
$users = [];

foreach ($pool->getItems(['user.1', 'user.2']) as $key => $item) {
    if ($item->isHit()) {
        $users[$key] = $item->get();
    }
}

$pool->deleteItem('user.1');
$pool->deleteItems(['user.2', 'user.3']);
```

Deleting a missing key is successful.

### Deferred writes

```php
foreach ([1, 2, 3] as $id) {
    $item = $pool->getItem('user.' . $id);
    $item->set(['id' => $id])->expiresAfter(600);

    if (! $pool->saveDeferred($item)) {
        throw new RuntimeException('A deferred item could not be queued.');
    }
}

if (! $pool->commit()) {
    throw new RuntimeException('One or more deferred items could not be saved.');
}
```

Pending items are visible through that pool before `commit()`. The pool attempts to commit remaining deferred items during destruction, but explicit `commit()` is recommended so failures can be handled.

## Cache tags

Tagging is available for any PSR-6 pool through `TaggablePsr6PoolAdapter`.

```php
use Qubus\Cache\InMemoryCache;
use Qubus\Cache\Psr6\TaggablePsr6PoolAdapter;

$basePool = new InMemoryCache(namespace: 'catalog');
$pool = TaggablePsr6PoolAdapter::makeTaggable($basePool);

$item = $pool->getItem('product.42');
$item
    ->set(['id' => 42, 'category' => 'keyboards'])
    ->setTags(['products', 'keyboards']);

$pool->save($item);

// Deletes every item carrying this tag.
$pool->invalidateTag('keyboards');

// Deletes items carrying either tag.
$pool->invalidateTags(['products', 'sale']);
```

`setTags()` replaces the item's current tag set. `getPreviousTags()` returns the tags loaded from the stored item, which is useful when changing tags.

A separate PSR-6 pool may store tag indexes:

```php
$items = new InMemoryCache(namespace: 'items');
$tagIndexes = new InMemoryCache(namespace: 'tag-indexes');

$pool = TaggablePsr6PoolAdapter::makeTaggable($items, $tagIndexes);
```

When a separate tag store is supplied, clearing the taggable pool clears both pools. Items passed to `save()` or `saveDeferred()` must originate from the taggable pool.

## Keys and namespaces

Cache keys must:

- Be non-empty strings.
- Contain at most 64 characters.
- Not contain any reserved character from `{}()/\@:`.

Letters, numbers, `_`, `.`, and other non-reserved characters are accepted. Public keys are SHA-1 hashed before being passed to a backend, preventing backend length differences and path traversal.

Namespaces isolate consumers sharing an adapter or backend. Namespaces containing 1–64 ASCII letters, digits, underscores, or hyphens are retained as written. Other namespace strings are hashed before use so they cannot alter filesystem paths, regular expressions, or Redis glob patterns.

Use stable, distinct namespaces for applications, tenants, environments, or cache schema versions:

```php
$production = new InMemoryCache(namespace: 'shop-production-v2');
$testing = new InMemoryCache(namespace: 'shop-testing-v2');
```

Changing a namespace intentionally produces cold cache misses and leaves old backend entries available for their normal expiry or pruning process.

## Values and serialization

Strings, integers, floats, booleans, `null`, arrays, binary strings, and serializable objects are supported.

```php
$cache->set('string', 'value');
$cache->set('integer', 42);
$cache->set('nullable', null);
$cache->set('array', ['enabled' => true]);
$cache->set('object', new DateTimeImmutable());
```

Avoid resources, closures, and objects that cannot safely be serialized. Classes used by cached objects must be autoloadable when values are restored. Filesystem and Redis/Predis storage should be accessible only to trusted application infrastructure because restoring PHP objects invokes PHP deserialization behavior.

## Error handling

Invalid keys and tags throw `Qubus\Cache\TypeException`, which implements both PSR invalid-argument exception interfaces:

```php
use Psr\SimpleCache\InvalidArgumentException;

try {
    $cache->set('invalid/key', 'value');
} catch (InvalidArgumentException $exception) {
    error_log($exception->getMessage());
}
```

Write, delete, bulk, commit, and prune methods return `false` when a handled backend operation fails. Backend clients may also throw their own transport or filesystem exceptions. Check boolean results where cache persistence matters, while keeping application behavior resilient to cache misses.

## Using adapters directly

The native facades are the simplest choice. Use `SimpleCache` and `ItemPool` directly when an adapter has no facade or when the two APIs need different defaults or namespaces:

```php
use Qubus\Cache\Adapter\InMemoryCacheAdapter;
use Qubus\Cache\Psr16\SimpleCache;
use Qubus\Cache\Psr6\ItemPool;

$adapter = new InMemoryCacheAdapter();

$simple = new SimpleCache($adapter, ttl: 60, namespace: 'simple');
$pool = new ItemPool(
    adapter: $adapter,
    ttl: 300,
    namespace: 'items',
    autoCommitCount: 100,
);
```

Custom adapters implement `Qubus\Cache\Adapter\CacheAdapter`. Adapter keys are already validated, hashed, and prefixed by the PSR wrappers. Bulk adapter methods use these conventions:

- `getMultiple(array $keys)` returns values in input order, using `null` for misses.
- `setMultiple(array $entries)` receives `['value' => mixed, 'ttl' => ?int]` for each storage key and returns `null` on complete success or failed storage keys.
- `deleteMultiple(array $keys)` returns `null` on complete success or failed storage keys.
- `purge(?string $pattern)` removes matching keys; `null` means the entire adapter store and may be destructive.

## Skeleton Application

It is questionable whether cache is necessary or helpful in an event-sourced system. Nevertheless, PSR-6 and PSR-16
cache implementations are available.

The default cache adapter used is `Qubus\Cache\Adapter\FileSystemCacheAdapter`. Predis/Redis, APCu, InMemory, and
Memcached adapters are also available. If you want to use another adapter, you can switch it out in
`Application\Provider\Psr16ServiceProvider`.

### Cache Service Provider

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

Other than PSR-6 and PSR-16 implementations, there are HTTP cache middlewares available to cache different aspects
of your application:

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
