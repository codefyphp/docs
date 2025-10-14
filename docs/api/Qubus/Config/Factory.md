***

# Factory





* Full name: `\Qubus\Config\Factory`
* This class implements:
[`\Interop\Config\RequiresMandatoryOptions`](../../Interop/Config/RequiresMandatoryOptions.md), [`\Interop\Config\RequiresConfig`](../../Interop/Config/RequiresConfig.md)


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`VENDOR_NAME`|public| |&#039;qubus&#039;|
|`PACKAGE_NAME`|public| |&#039;config&#039;|


## Methods


### __invoke



```php
public __invoke(array|\Qubus\Config\Configuration $config): \Qubus\Config\Collection
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$config` | **array&#124;\Qubus\Config\Configuration** |  |




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


***
> Automatically generated on 2025-10-13
