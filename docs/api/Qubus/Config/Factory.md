# Factory

***

* Full name: `\Qubus\Config\Factory`
* This class implements:
  `RequiresMandatoryOptions`,
  `RequiresConfig`

## Constants

| Constant       | Visibility | Type | Value    |
|----------------|------------|------|----------|
| `VENDOR_NAME`  | public     |      | 'qubus'  |
| `PACKAGE_NAME` | public     |      | 'config' |

## Methods

### __invoke

```php
public __invoke(array|\Qubus\Config\Configuration $config): \Qubus\Config\Collection
```

**Parameters:**

| Parameter | Type                                   | Description |
|-----------|----------------------------------------|-------------|
| `$config` | **array\|\Qubus\Config\Configuration** |             |

**Throws:**

- [`PathNotFoundException`](./Path/PathNotFoundException.md)

***

### vendorName

```php
public vendorName(): string
```

***

### packageName

```php
public packageName(): string
```

***

### mandatoryOptions

```php
public mandatoryOptions(): string[]
```

**Return Value:**

List with mandatory options

***

### optionalOptions

```php
public optionalOptions(): string[]
```

**Return Value:**

List with optional options

***

### dimensions

```php
public dimensions(): iterable
```

***
