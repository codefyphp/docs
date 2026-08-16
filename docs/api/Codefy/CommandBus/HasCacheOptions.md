# HasCacheOptions

***

* Full name: `\Codefy\CommandBus\HasCacheOptions`
* Parent interfaces:
  [`\Codefy\CommandBus\CacheableCommand`](./CacheableCommand.md)

## Methods

### getCacheExpiry

In how many seconds from now should this cache item expire.

```php
public getCacheExpiry(): int|null
```

Return null to use the default value specified in the CachingDecorator.

***

### getCacheKey

The cache key used when caching this object. Return null to
automatically generate a cache key.

```php
public getCacheKey(): string|null
```

***
