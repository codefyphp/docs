# ValueExtractorAware

Borrowed from ramsey/collection.

Provides functionality to extract the value of a property or method from an object.

***

* Full name: `\Qubus\Support\Collection\ValueExtractorAware`

## Methods

### extractValue

Extracts the value of the given property or method from the object.

```php
protected extractValue(mixed $object, string|null $propertyOrMethod = null): mixed
```

**Parameters:**

| Parameter           | Type             | Description                                                     |
|---------------------|------------------|-----------------------------------------------------------------|
| `$object`           | **mixed**        | The object to extract the value from.                           |
| `$propertyOrMethod` | **string\|null** | The property or method for which the
value should be extracted. |

**Return Value:**

the value extracted from the specified property or method.

**Throws:**

if the method or property is not defined.
- [`ValueExtractionException`](./ValueExtractionException.md)

***
