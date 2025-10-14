***

# BaseTransformer





* Full name: `\Qubus\Support\Serializer\Transformer\BaseTransformer`
* This class implements:
[`\Qubus\Support\Serializer\Strategy\Strategy`](../Strategy/Strategy.md)
* This class is an **Abstract class**




## Methods


### recursiveUnset



```php
protected recursiveUnset(array& $array, array $unwantedKey): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** |  |
| `$unwantedKey` | **array** |  |





***

### recursiveSetValues



```php
protected recursiveSetValues(array& $array): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** |  |





***

### recursiveFlattenOneElementObjectsToScalarType



```php
protected recursiveFlattenOneElementObjectsToScalarType(array& $array, null $parentKey = null, null $currentKey = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** |  |
| `$parentKey` | **null** |  |
| `$currentKey` | **null** |  |





***

### unserialize



```php
public unserialize(mixed $value): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **mixed** |  |




**Throws:**

- [`TypeException`](../../../Exception/Data/TypeException.md)



***


***
> Automatically generated on 2025-10-13
