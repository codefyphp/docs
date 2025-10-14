***

# Serializable





* Full name: `\Qubus\Support\Serializer\Serializable`



## Methods


### serialize

Serializes data if necessary.

```php
public serialize(string|array|object $data): bool|string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **string&#124;array&#124;object** | Data to be serialized. |


**Return Value:**

Serialized data or original string.



**Throws:**

- [`SerializerException`](./SerializerException.md)



***

### unserialize

Unserializes data if necessary.

```php
public unserialize(string|array|object $data): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **string&#124;array&#124;object** | Data that should be unserialzed. |


**Return Value:**

Unserialized data or original string.




***


***
> Automatically generated on 2025-10-13
