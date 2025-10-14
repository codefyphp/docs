***

# AwsS3FlysystemAdapter





* Full name: `\Qubus\FileSystem\Adapter\AwsS3FlysystemAdapter`
* Parent class: [`AwsS3V3Adapter`](../../../League/Flysystem/AwsS3V3/AwsS3V3Adapter.md)
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
public __construct(\Aws\S3\S3ClientInterface $client, \Qubus\Config\ConfigContainer $config): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$client` | **\Aws\S3\S3ClientInterface** |  |
| `$config` | **\Qubus\Config\ConfigContainer** |  |




**Throws:**

- [`Exception`](../../Exception/Exception.md)



***


***
> Automatically generated on 2025-10-13
