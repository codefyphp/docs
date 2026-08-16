# ValueToStringAware

Borrowed from ramsey/collection.

***

* Full name: `\Qubus\Support\Collection\ValueToStringAware`

## Methods

### toolValueToString

Returns a string representation of the value.

```php
protected toolValueToString(mixed $value = null): string
```

- null value: `'NULL'`
- boolean: `'TRUE'`, `'FALSE'`
- array: `'Array'`
- scalar: converted-value
- resource: `'(type resource #number)'`
- object with `__toString()`: result of `__toString()`
- object DateTime: ISO 8601 date
- object: `'(className Object)'`
- anonymous function: same as object

**Parameters:**

| Parameter | Type      | Description                      |
|-----------|-----------|----------------------------------|
| `$value`  | **mixed** | the value to return as a string. |

***
