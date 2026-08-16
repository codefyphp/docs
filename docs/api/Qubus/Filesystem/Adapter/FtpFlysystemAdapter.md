# FtpFlysystemAdapter

***

* Full name: `\Qubus\FileSystem\Adapter\FtpFlysystemAdapter`
* Parent class: [`FtpAdapter`](../../../League/Flysystem/Ftp/FtpAdapter.md)
* This class is marked as **final** and can't be subclassed
* This class implements:
  `FilesystemAdapter`
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
public __construct(\Qubus\Config\ConfigContainer $config): mixed
```

**Parameters:**

| Parameter | Type                              | Description |
|-----------|-----------------------------------|-------------|
| `$config` | **\Qubus\Config\ConfigContainer** |             |

**Throws:**

- [`Exception`](../../Exception/Exception.md)

***

### setFtpConnectionOptions

FTP connection options.

```php
private setFtpConnectionOptions(): array{host: string, root: string, username: string, password: string, port: int, ssl: bool, timeout: int, utf8: bool, passive: bool, transferMode: int, systemType: ?string, ignorePassiveAddress: ?bool, timestampsOnUnixListingsEnabled: bool, recurseManually: bool}
```

**Throws:**

- [`Exception`](../../Exception/Exception.md)

***
