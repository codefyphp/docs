***

# TaggableCacheItem

An item that supports tags. This interface is a soon-to-be-PSR.



* Full name: `\Qubus\Cache\Psr6\TaggableCacheItem`
* Parent interfaces: [`CacheItemInterface`](../../../Psr/Cache/CacheItemInterface.md)


## Methods


### getPreviousTags

Get all existing tags. These are the tags the item has when the item is
returned from the pool.

```php
public getPreviousTags(): array
```












***

### setTags

Overwrite all tags with a new set of tags.

```php
public setTags(string[] $tags): \Qubus\Cache\Psr6\TaggableCacheItem
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$tags` | **string[]** | An array of tags |




**Throws:**
<p>When a tag is not valid.</p>

- [`InvalidArgumentException`](../../../Psr/Cache/InvalidArgumentException.md)



***


***
> Automatically generated on 2025-10-13
