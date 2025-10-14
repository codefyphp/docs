***

# ArrayHelper





* Full name: `\Qubus\Support\ArrayHelper`




## Methods


### get

Gets a dot-notated key from an array, with a default value if it does
not exist.

```php
public get(array|\ArrayAccess $array, mixed|null $key = null, string|null $default = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array&#124;\ArrayAccess** | $array The search array. |
| `$key` | **mixed&#124;null** | The dot-notated key or array of keys. |
| `$default` | **string&#124;null** | The default value |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### set

Set an array item (dot-notated) to the value.

```php
public set(array& $array, mixed $key, mixed|null $value = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** | The array to insert it into |
| `$key` | **mixed** | The dot-notated key to set or array of keys |
| `$value` | **mixed&#124;null** | The value |





***

### pluck

Pluck an array of values from an array.

```php
public pluck(array $array, string $key, bool|int|string|null $index = null): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** | Collection of arrays to pluck from. |
| `$key` | **string** | Key of the value to pluck. |
| `$index` | **bool&#124;int&#124;string&#124;null** | Optional return array index key, true for original index. |


**Return Value:**

Array of plucked values.



**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### keyExists

Array_key_exists with a dot-notated key from an array.

```php
public keyExists(array|\ArrayAccess $array, mixed $key): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array&#124;\ArrayAccess** | $array The search array |
| `$key` | **mixed** | The dot-notated key or array of keys |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### delete

Unsets dot-notated k?string ey from an array

```php
public delete(array& $array, mixed|null $key = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** | The search array |
| `$key` | **mixed&#124;null** | The dot-notated key or array of keys |





***

### assocToKeyVal

Converts a multidimensional associative array into an array of key => values with the provided field names.

```php
public assocToKeyVal(array|\Iterator $assoc, string $keyField, string $valField): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$assoc` | **array&#124;\Iterator** | The array to convert. |
| `$keyField` | **string** | The field name of the key field. |
| `$valField` | **string** | The field name of the value field. |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### keyValToAssoc

Converts an array of key => values into a multidimensional associative array with the provided field names

```php
public keyValToAssoc(array|\Iterator $array, string $keyField, string $valField): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array&#124;\Iterator** | $array      the array to convert |
| `$keyField` | **string** | the field name of the key field |
| `$valField` | **string** | the field name of the value field |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### toAssoc

Converts the given 1 dimensional non-associative array to an associative
array.

```php
public toAssoc(array $arr): array|null
```

The array given must have an even number of elements or null will be returned.

$this->toAssoc(['foo','bar']);






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$arr` | **array** | the array to change |


**Return Value:**

the new array or null



**Throws:**

- [`BadMethodCallException`](../../BadMethodCallException.md)



***

### isAssoc

Checks if the given array is an assoc array.

```php
public isAssoc(array $arr): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$arr` | **array** | the array to check |


**Return Value:**

True if it's an assoc array, false if not.




***

### flatten

Flattens a multi-dimensional associative array down into a 1 dimensional
associative array.

```php
public flatten(array $array, string $glue = &#039;:&#039;, bool $reset = true, bool $indexed = true): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** | the array to flatten |
| `$glue` | **string** | what to glue the keys together with |
| `$reset` | **bool** | whether to reset and start over on a new array |
| `$indexed` | **bool** | whether to flatten only associative array&#039;s, or also indexed ones |





***

### flattenAssoc

Flattens a multi-dimensional associative array down into a 1 dimensional
associative array.

```php
public flattenAssoc(array $array, string $glue = &#039;:&#039;, bool $reset = true): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** | the array to flatten |
| `$glue` | **string** | what to glue the keys together with |
| `$reset` | **bool** | whether to reset and start over on a new array |





***

### reverseFlatten

Reverse a flattened array in its original form.

```php
public reverseFlatten(array $array, string $glue = &#039;:&#039;): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** | flattened array |
| `$glue` | **string** | glue used in flattening |


**Return Value:**

The unflattened array.




***

### filterPrefixed

Filters an array on prefixed associative keys.

```php
public filterPrefixed(array $array, string $prefix, bool $removePrefix = true): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** | The array to filter. |
| `$prefix` | **string** | Prefix to filter on. |
| `$removePrefix` | **bool** | Whether to remove the prefix. |





***

### filterRecursive

Recursive version of PHP's array_filter().

```php
public filterRecursive(array $array, callable|null $callback = null): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** | The array to filter. |
| `$callback` | **callable&#124;null** | $callback The callback that determines whether a value is filtered. |





***

### removePrefixed

Removes items from an array that match a key prefix.

```php
public removePrefixed(array $array, string $prefix): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** | The array to remove from. |
| `$prefix` | **string** | Prefix to filter on. |





***

### filterSuffixed

Filters an array on suffixed associative keys.

```php
public filterSuffixed(array $array, string $suffix, bool $removeSuffix = true): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** | The array to filter. |
| `$suffix` | **string** | Suffix to filter on. |
| `$removeSuffix` | **bool** | Whether to remove the suffix. |





***

### removeSuffixed

Removes items from an array that match a key suffix.

```php
public removeSuffixed(array $array, string $suffix): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** | The array to remove from. |
| `$suffix` | **string** | Suffix to filter on. |





***

### filterKeys

Filters an array by an array of keys

```php
public filterKeys(array $array, array $keys, bool $remove = false): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** | The array to filter. |
| `$keys` | **array** | The keys to filter |
| `$remove` | **bool** | If true, removes the matched elements. |





***

### insert

Insert value(s) into an array, mostly an array_splice alias.

```php
public insert(array& $original, mixed $value, int $pos): bool
```

WARNING: original array is edited by reference, only bool success is returned.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$original` | **array** | The original array (by reference). |
| `$value` | **mixed** | The value(s) to insert, if you want to insert an array<br />it needs to be in an array itself. |
| `$pos` | **int** | The numeric position at which to insert, negative to count from the end backwards. |


**Return Value:**

False when array shorter than $pos, otherwise true




***

### insertAssoc

Insert value(s) into an array, mostly an array_splice alias
WARNING: original array is edited by reference, only bool success is returned

```php
public insertAssoc(array& $original, mixed $values, int $pos): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$original` | **array** | The original array (by reference) |
| `$values` | **mixed** | The value(s) to insert, if you want to insert an array<br />it needs to be in an array itself. |
| `$pos` | **int** | The numeric position at which to insert, negative to count from the end backwards. |


**Return Value:**

false when array shorter than $pos, otherwise true




***

### insertBeforeKey

Insert value(s) into an array before a specific key.

```php
public insertBeforeKey(array& $original, mixed $value, int|string $key, bool $isAssoc = false): bool
```

WARNING: original array is edited by reference, only bool success is returned.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$original` | **array** | The original array (by reference). |
| `$value` | **mixed** | The value(s) to insert, if you want to insert an array<br />it needs to be in an array itself. |
| `$key` | **int&#124;string** | The key before which to insert. |
| `$isAssoc` | **bool** | Whether the input is an associative array. |


**Return Value:**

False when key isn't found in the array, otherwise true.




***

### insertAfterKey

Insert value(s) into an array after a specific key.

```php
public insertAfterKey(array& $original, mixed $value, int|string $key, bool $isAssoc = false): bool
```

WARNING: original array is edited by reference, only bool success is returned.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$original` | **array** | The original array (by reference). |
| `$value` | **mixed** | The value(s) to insert, if you want to insert an array<br />it needs to be in an array itself. |
| `$key` | **int&#124;string** | The key after which to insert. |
| `$isAssoc` | **bool** | Whether the input is an associative array. |


**Return Value:**

False when key isn't found in the array, otherwise true.




***

### insertAfterValue

Insert value(s) into an array after a specific value (first found in array).

```php
public insertAfterValue(array& $original, mixed $value, int|string $search, bool $isAssoc = false): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$original` | **array** | The original array (by reference). |
| `$value` | **mixed** | The value(s) to insert, if you want to insert an array<br />it needs to be in an array itself. |
| `$search` | **int&#124;string** | The value after which to insert. |
| `$isAssoc` | **bool** | Whether the input is an associative array. |


**Return Value:**

False when value isn't found in the array, otherwise true.




***

### insertBeforeValue

Insert value(s) into an array before a specific value (first found in array)

```php
public insertBeforeValue(array& $original, mixed $value, int|string $search, bool $isAssoc = false): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$original` | **array** | The original array (by reference). |
| `$value` | **mixed** | The value(s) to insert, if you want to insert an array.<br />it needs to be in an array itself. |
| `$search` | **int&#124;string** | The value after which to insert. |
| `$isAssoc` | **bool** | Whether the input is an associative array. |


**Return Value:**

False when value isn't found in the array, otherwise true.




***

### sort

Sorts a multi-dimensional array by it's values.

```php
public sort(array $array, string $key, string $order = &#039;asc&#039;, int $sortFlags = SORT_REGULAR): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** | The array to fetch from. |
| `$key` | **string** | The key to sort by. |
| `$order` | **string** | The order (asc or desc). |
| `$sortFlags` | **int** | The php sort type flag. |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### multisort

Sorts an array on multiple values, with deep sorting support.

```php
public multisort(array $array, array $conditions, bool $ignoreCase = false): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** | Collection of arrays/objects to sort. |
| `$conditions` | **array** | Sorting conditions. |
| `$ignoreCase` | **bool** | Whether to sort case-insensitive. |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### average

Find the average of an array.

```php
public average(array $array): float|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** | The array containing the values. |


**Return Value:**

The average value.




***

### replaceKey

Replaces key names in an array by names in the $replace parameter.

```php
public replaceKey(array $source, array|string $replace, string|null $newKey = null): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$source` | **array** | The array containing the key/value combinations |
| `$replace` | **array&#124;string** | Key to replace or array containing the replacement keys |
| `$newKey` | **string&#124;null** | The replacement key |


**Return Value:**

The array with the new keys.




***

### merge

Merge 2 arrays recursively, differs in 2 important ways from array_merge_recursive().

```php
public merge(): array
```

When there's 2 different values and not both arrays, the latter value overwrites the earlier
instead of merging both into an array.

Numeric keys that don't conflict aren't changed, only when a numeric key already exists is the
value added using array_push().









**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### mergeAssoc

Merge 2 arrays recursively, differs in 2 important ways from array_merge_recursive().

```php
public mergeAssoc(): array
```

When there's 2 different values and not both arrays, the latter value overwrites the earlier
instead of merging both into an array. Numeric keys are never changed.









**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### prepend

Prepends a value with an associative key to an array.

```php
public prepend(array& $arr, array|string $key, mixed|null $value = null): string|array
```

Will overwrite if the value exists.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$arr` | **array** | The array to prepend to |
| `$key` | **array&#124;string** | The key or array of keys and values |
| `$value` | **mixed&#124;null** | The value to prepend |





***

### inArrayRecursive

Recursive in_array

```php
public inArrayRecursive(mixed $needle, array $haystack, bool $strict = false): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$needle` | **mixed** | What to search for. |
| `$haystack` | **array** | Array to search in. |
| `$strict` | **bool** |  |


**Return Value:**

Whether the needle is found in the haystack.




***

### isMulti

Checks if the given array is a multidimensional array.

```php
public isMulti(array $arr, bool $allKeys = false): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$arr` | **array** | The array to check |
| `$allKeys` | **bool** | If true, check that all elements are arrays. |


**Return Value:**

True if its a multidimensional array, false if not.




***

### search

Searches the array for a given value and returns the
corresponding key or default value.

```php
public search(array|\ArrayAccess $array, mixed $value, string|int|null $default = null, bool $recursive = true, string $delimiter = &#039;.&#039;, bool $strict = false): string|bool|null|int
```

If $recursive is set to true, then the $this->search()
method will return a delimiter-notated key using the
$delimiter parameter.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array&#124;\ArrayAccess** | $array     The search array. |
| `$value` | **mixed** | The searched value. |
| `$default` | **string&#124;int&#124;null** | The default value. |
| `$recursive` | **bool** | Whether to get keys recursive. |
| `$delimiter` | **string** | The delimiter, when $recursive is true. |
| `$strict` | **bool** | If true, do a strict key comparison. |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### unique

Returns only unique values in an array. It does not sort. First value is used.

```php
public unique(array $arr): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$arr` | **array** | The array to dedupe. |


**Return Value:**

array With only de-duped values.




***

### sum

Calculate the sum of an array.

```php
public sum(array|\ArrayAccess $array, string $key): float|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array&#124;\ArrayAccess** | $array The array containing the values. |
| `$key` | **string** | Key of the value to pluck. |


**Return Value:**

The sum value



**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### reindex

Returns the array with all numeric keys re-indexed, and string keys untouched.

```php
public reindex(array $arr): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$arr` | **array** | The array to reindex. |


**Return Value:**

Re-indexed array.




***

### previousByKey

Get the previous value or key from an array using the current array key.

```php
public previousByKey(array|\ArrayAccess $array, mixed $key, bool $getValue = false, bool $strict = false): string|bool|null|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array&#124;\ArrayAccess** | $array    The array containing the values. |
| `$key` | **mixed** | Key of the current entry to use as reference. |
| `$getValue` | **bool** | If true, return the previous value instead of the previous key. |
| `$strict` | **bool** | If true, do a strict key comparison. |


**Return Value:**

The value in the array, null if there is no previous value,
or false if the key doesn't exist.



**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### nextByKey

Get the next value or key from an array using the current array key.

```php
public nextByKey(array|\ArrayAccess $array, mixed $key, bool $getValue = false, bool $strict = false): string|bool|null|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array&#124;\ArrayAccess** | $array The array containing the values. |
| `$key` | **mixed** | Key of the current entry to use as reference. |
| `$getValue` | **bool** | If true, return the next value instead of the next key. |
| `$strict` | **bool** | If true, do a strict key comparison. |


**Return Value:**

The value in the array, null if there is no next value,
or false if the key doesn't exist.



**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### previousByValue

Get the previous value or key from an array using the current array value

```php
public previousByValue(array|\ArrayAccess $array, mixed $value, bool $getValue = true, bool $strict = false): string|bool|null|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array&#124;\ArrayAccess** | $array    The array containing the values. |
| `$value` | **mixed** | Value of the current entry to use as reference. |
| `$getValue` | **bool** | If true, return the previous value instead of the previous key. |
| `$strict` | **bool** | If true, do a strict key comparison. |


**Return Value:**

The value in the array, null if there is no previous value,
or false if the key doesn't exist.



**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### nextByValue

Get the next value or key from an array using the current array value.

```php
public nextByValue(array|\ArrayAccess $array, mixed $value, bool $getValue = true, bool $strict = false): string|bool|null|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array&#124;\ArrayAccess** | $array    The array containing the values. |
| `$value` | **mixed** | Value of the current entry to use as reference. |
| `$getValue` | **bool** | If true, return the next value instead of the next key. |
| `$strict` | **bool** | If true, do a strict key comparison. |


**Return Value:**

The value in the array, null if there is no next value,
or false if the key doesn't exist



**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### subset

Return the subset of the array defined by the supplied keys.

```php
public subset(array $array, array $keys, mixed|null $default = null): array
```

Returns $default for missing keys, as with $this->get().






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** | The array containing the values. |
| `$keys` | **array** | List of keys (or indices) to return. |
| `$default` | **mixed&#124;null** | Value of missing keys; default null. |


**Return Value:**

An array containing the same set of keys provided.



**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### value

Takes a value and checks if it is a Closure or not, if it is it
will return the result of the closure, if not, it will simply return the
value.

```php
public value(mixed $var): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$var` | **mixed** | The value to get. |





***


***
> Automatically generated on 2025-10-13
