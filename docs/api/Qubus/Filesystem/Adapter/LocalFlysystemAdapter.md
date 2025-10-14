***

# LocalFlysystemAdapter





* Full name: `\Qubus\FileSystem\Adapter\LocalFlysystemAdapter`
* Parent class: [`LocalFilesystemAdapter`](../../../League/Flysystem/Local/LocalFilesystemAdapter.md)
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\League\Flysystem\FilesystemAdapter`](../../../League/Flysystem/FilesystemAdapter.md)
* This class is a **Final class**



## Properties


### config



```php
public \Qubus\Config\ConfigContainer $config
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Config\ConfigContainer $config, ?string $location = null, int $writeFlags = LOCK_EX, int $linkHandling = self::DISALLOW_LINKS, ?\League\MimeTypeDetection\MimeTypeDetector $mimeTypeDetector = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$config` | **\Qubus\Config\ConfigContainer** |  |
| `$location` | **?string** |  |
| `$writeFlags` | **int** |  |
| `$linkHandling` | **int** |  |
| `$mimeTypeDetector` | **?\League\MimeTypeDetection\MimeTypeDetector** |  |




**Throws:**

- [`Exception`](../../Exception/Exception.md)



***

### setVisibilityConverter

The directory and file visibility options.

```php
private setVisibilityConverter(): array
```











**Throws:**

- [`Exception`](../../Exception/Exception.md)



***


***
> Automatically generated on 2025-10-13
