# Attr

HTML attributes

***

* Full name: `\Qubus\Form\FormBuilder\Attr`
* Parent class: [`ArrayIterator`](../../../ArrayIterator.md)

## Methods

### __construct

```php
public __construct(array $array = []): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$array`  | **array** |             |

***

### cast

Cast the value of an attribute to a string.

```php
protected cast(string $key, mixed $value): bool|string|null
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |
| `$value`  | **mixed**  |             |

***

### castClass

Cast the value of an attribute to a string.

```php
protected castClass(array $values): string|null
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$values` | **array** |             |

***

### set

Set HTML attribute(s).

```php
public set(array|string $attr, mixed|null $value = null): \Qubus\Form\FormBuilder\Attr
```

**Parameters:**

| Parameter | Type              | Description                                   |
|-----------|-------------------|-----------------------------------------------|
| `$attr`   | **array\|string** | Attribute name or assoc array with attributes |
| `$value`  | **mixed\|null**   |                                               |

**Return Value:**

$this

***

### get

Get an HTML attribute(s).

```php
final public get(string|null $attr = null): string|array|null
```

All attributes will be cased to their string representation.

* This method is **final**.
**Parameters:**

| Parameter | Type             | Description                                |
|-----------|------------------|--------------------------------------------|
| `$attr`   | **string\|null** | Attribute name, omit to get all attributes |

***

### getRaw

Get an HTML attribute(s) without casting them.

```php
final public getRaw(string|null $attr = null): mixed
```

* This method is **final**.
**Parameters:**

| Parameter | Type             | Description                                |
|-----------|------------------|--------------------------------------------|
| `$attr`   | **string\|null** | Attribute name, omit to get all attributes |

***

### getAll

Get all HTML attributes.

```php
protected getAll(bool $raw = false): array
```

**Parameters:**

| Parameter | Type     | Description           |
|-----------|----------|-----------------------|
| `$raw`    | **bool** | Don't cast attributes |

***

### hasClass

Check if class is present

```php
public hasClass(string $class): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$class`  | **string** |             |

***

### addClass

Add a class

```php
public addClass(array|string $class): void
```

**Parameters:**

| Parameter | Type              | Description                                                 |
|-----------|-------------------|-------------------------------------------------------------|
| `$class`  | **array\|string** | Multiple classes may be specified as array or using a space |

***

### removeClass

Remove a class

```php
public removeClass(array|string $class): \Qubus\Form\FormBuilder\Attr
```

**Parameters:**

| Parameter | Type              | Description                                                 |
|-----------|-------------------|-------------------------------------------------------------|
| `$class`  | **array\|string** | Multiple classes may be specified as array or using a space |

**Return Value:**

$this

***

### render

Get attributes as string

```php
public render(array $override = []): string
```

**Parameters:**

| Parameter   | Type      | Description                   |
|-------------|-----------|-------------------------------|
| `$override` | **array** | Attributes to add or override |

***

### renderOnly

Get specific attributes as string

```php
public renderOnly(array|string $attrs): string
```

**Parameters:**

| Parameter | Type              | Description |
|-----------|-------------------|-------------|
| `$attrs`  | **array\|string** |             |

***

### __toString

Get attributes as string

```php
final public __toString(): string
```

* This method is **final**.
***

### offsetGet

Get value for an offset

```php
public offsetGet(string $index): string|null
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$index`  | **string** |             |

***

### offsetUnset

Unset value at offset

```php
public offsetUnset(mixed $index): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$index`  | **mixed** |             |

***

### offsetSet

Set value for an offset

```php
public offsetSet(mixed $index, mixed $newval): void
```

**Parameters:**

| Parameter | Type      | Description                          |
|-----------|-----------|--------------------------------------|
| `$index`  | **mixed** | The index to set for.                |
| `$newval` | **mixed** | The new value to store at the index. |

***

### append

Append a value.

```php
final public append(mixed $value): void
```

* This method is **final**.
**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

**Throws:**

- [`Exception`](../../Exception/Exception.md)

***

### appendAttr

Add a key/value as HTML attribute.

```php
protected static appendAttr(array& $pairs, string $key, mixed $value): void
```

* This method is **static**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$pairs`  | **array**  |             |
| `$key`    | **string** |             |
| `$value`  | **mixed**  | Scalar      |

***
