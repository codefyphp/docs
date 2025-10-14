***

# TaggableCacheItemPool

Interface for invalidating cached items using tags. This interface is a soon-to-be-PSR.



* Full name: `\Qubus\Cache\Psr6\TaggableCacheItemPool`
* Parent interfaces: [`CacheItemPoolInterface`](../../../Psr/Cache/CacheItemPoolInterface.md)


## Methods


### invalidateTag

Invalidates cached items using a tag.

```php
public invalidateTag(string $tag): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$tag` | **string** | The tag to invalidate |


**Return Value:**

True on success



**Throws:**
<p>When $tags is not valid.</p>

- [`InvalidArgumentException`](../../../Psr/Cache/InvalidArgumentException.md)



***

### invalidateTags

Invalidates cached items using tags.

```php
public invalidateTags(string[] $tags): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$tags` | **string[]** | An array of tags to invalidate |


**Return Value:**

True on success



**Throws:**
<p>When $tags is not valid.</p>

- [`InvalidArgumentException`](../../../Psr/Cache/InvalidArgumentException.md)



***


***
> Automatically generated on 2025-10-13
