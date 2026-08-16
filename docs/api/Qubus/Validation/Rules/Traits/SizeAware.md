# SizeAware

***

* Full name: `\Qubus\Validation\Rules\Traits\SizeAware`

## Methods

### getValueSize

Get size (int) value from given $value

```php
protected getValueSize(mixed $value): float|false
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***
### getBytesSize

Given $size and get the bytes

```php
protected getBytesSize(mixed $size): float
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$size`   | **mixed** |             |

**Throws:**

- [`InvalidArgumentException`](../../../../InvalidArgumentException.md)

***
### isUploadedFileValue

Check whether value is from $_FILES

```php
public isUploadedFileValue(mixed $value): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***
