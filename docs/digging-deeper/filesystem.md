---
title: File Storage
sidebar_title: File Storage
order: 23
---

## Requirements

- PHP 8.4 or newer
- The cURL and FTP PHP extensions

The appropriate network credentials and PHP extensions are also required when using S3 or SFTP.

## Installation

```shell
composer require qubus/filesystem
```

## Introduction

The filesystem is a wrapper for [PHP League’s Flysystem](https://github.com/thephpleague/Flysystem) by Frank de Jonge. 
The filesystem includes adapters for working with local filesystems, SFTP, and Amazon S3.

## Quick start

Create a configuration container, select an adapter, and pass the adapter to `FileSystem`:

```php
<?php

declare(strict_types=1);

use Qubus\Config\Collection;
use Qubus\FileSystem\Adapter\LocalFlysystemAdapter;
use Qubus\FileSystem\FileSystem;

require __DIR__ . '/vendor/autoload.php';

$config = new Collection([]);
$config->setConfigKey('filesystem', [
    'disks' => [
        'local' => [
            'root' => __DIR__ . '/storage',
        ],
    ],
]);

$filesystem = new FileSystem(new LocalFlysystemAdapter($config));

$filesystem->write('documents/example.txt', 'Hello from Qubus!');

echo $filesystem->read('documents/example.txt');
```

Paths passed to inherited Flysystem methods are relative to the adapter root. In this example, `documents/example.txt` resolves beneath `storage/`.

## Creating a filesystem

The constructor accepts a Flysystem adapter, optional default Flysystem operation configuration, and an optional path normalizer:

```php
$filesystem = new FileSystem(
    adapter: $adapter,
    configArray: ['visibility' => 'private'],
    pathNormalizer: null,
);
```

`configArray` configures Flysystem operations. Adapter connection settings belong in the `ConfigContainer` supplied to the adapter.

## Adapters

### Local storage

```php
use Qubus\Config\Collection;
use Qubus\FileSystem\Adapter\LocalFlysystemAdapter;
use Qubus\FileSystem\FileSystem;

$config = new Collection([]);
$config->setConfigKey('filesystem', [
    'disks' => [
        'local' => [
            'root' => __DIR__ . '/storage',
            'permission' => [
                'file' => [
                    'public' => 0644,
                    'private' => 0600,
                ],
                'dir' => [
                    'public' => 0755,
                    'private' => 0700,
                ],
            ],
        ],
    ],
]);

$adapter = new LocalFlysystemAdapter($config);
$filesystem = new FileSystem($adapter);
```

You can override the configured root when constructing the adapter:

```php
$adapter = new LocalFlysystemAdapter(
    config: $config,
    location: __DIR__ . '/temporary-storage',
);
```

| Configuration key                                | Type     | Default    |
|--------------------------------------------------|----------|------------|
| `filesystem.disks.local.root`                    | `string` | `/var/www` |
| `filesystem.disks.local.permission.file.public`  | `int`    | `0644`     |
| `filesystem.disks.local.permission.file.private` | `int`    | `0600`     |
| `filesystem.disks.local.permission.dir.public`   | `int`    | `0755`     |
| `filesystem.disks.local.permission.dir.private`  | `int`    | `0700`     |

### In-memory storage

The in-memory adapter is useful for tests, previews, and short-lived data. Its contents disappear when the adapter instance is discarded.

```php
use Qubus\Config\Collection;
use Qubus\FileSystem\Adapter\InMemoryFlysystemAdapter;
use Qubus\FileSystem\FileSystem;

$config = new Collection([]);
$config->setConfigKey('filesystem', [
    'disks' => [
        'inmemory' => [
            'visibility' => 'private',
        ],
    ],
]);

$filesystem = new FileSystem(new InMemoryFlysystemAdapter($config));
```

| Configuration key                      | Type     | Default  |
|----------------------------------------|----------|----------|
| `filesystem.disks.inmemory.visibility` | `string` | `public` |

### FTP storage

```php
use Qubus\Config\Collection;
use Qubus\FileSystem\Adapter\FtpFlysystemAdapter;
use Qubus\FileSystem\FileSystem;

$config = new Collection([]);
$config->setConfigKey('filesystem', [
    'disks' => [
        'ftp' => [
            'host' => 'ftp.example.com',
            'root' => '/uploads',
            'username' => 'application',
            'password' => $_ENV['FTP_PASSWORD'],
            'port' => 21,
            'ssl' => true,
            'timeout' => 30,
            'passive' => true,
        ],
    ],
]);

$filesystem = new FileSystem(new FtpFlysystemAdapter($config));
```

| Configuration key                           | Type      | Default      |
|---------------------------------------------|-----------|--------------|
| `filesystem.disks.ftp.host`                 | `string`  | `localhost`  |
| `filesystem.disks.ftp.root`                 | `string`  | `/var/www/`  |
| `filesystem.disks.ftp.username`             | `string`  | `root`       |
| `filesystem.disks.ftp.password`             | `string`  | `root`       |
| `filesystem.disks.ftp.port`                 | `int`     | `21`         |
| `filesystem.disks.ftp.ssl`                  | `bool`    | `false`      |
| `filesystem.disks.ftp.timeout`              | `int`     | `90`         |
| `filesystem.disks.ftp.utf8`                 | `bool`    | `false`      |
| `filesystem.disks.ftp.passive`              | `bool`    | `true`       |
| `filesystem.disks.ftp.transferMode`         | `int`     | `FTP_BINARY` |
| `filesystem.disks.ftp.systemType`           | `?string` | `null`       |
| `filesystem.disks.ftp.ignorePassiveAddress` | `?bool`   | `null`       |
| `filesystem.disks.ftp.enableTimestamps`     | `bool`    | `false`      |
| `filesystem.disks.ftp.recurseManually`      | `bool`    | `true`       |

FTP connections are not encrypted unless `ssl` is enabled and supported by the server. Prefer SFTP where possible.

### SFTP storage

Password authentication:

```php
use Qubus\Config\Collection;
use Qubus\FileSystem\Adapter\SftpFlysystemAdapter;
use Qubus\FileSystem\FileSystem;

$config = new Collection([]);
$config->setConfigKey('filesystem', [
    'disks' => [
        'sftp' => [
            'host' => 'sftp.example.com',
            'root' => '/uploads',
            'username' => 'application',
            'password' => $_ENV['SFTP_PASSWORD'],
            'port' => 22,
            'timeout' => 10,
            'maxtries' => 4,
            'fingerprint' => $_ENV['SFTP_HOST_FINGERPRINT'],
        ],
    ],
]);

$filesystem = new FileSystem(new SftpFlysystemAdapter($config));
```

Private-key authentication uses the same adapter:

```php
$config->setConfigKey('filesystem', [
    'disks' => [
        'sftp' => [
            'host' => 'sftp.example.com',
            'username' => 'application',
            'privatekey' => $_ENV['SFTP_PRIVATE_KEY'],
            'passphrase' => $_ENV['SFTP_KEY_PASSPHRASE'] ?? null,
            'fingerprint' => [
                $_ENV['SFTP_CURRENT_HOST_FINGERPRINT'],
                $_ENV['SFTP_NEXT_HOST_FINGERPRINT'],
            ],
        ],
    ],
]);
```

| Configuration key                               | Type                            | Default     |
|-------------------------------------------------|---------------------------------|-------------|
| `filesystem.disks.sftp.host`                    | `string`                        | `localhost` |
| `filesystem.disks.sftp.root`                    | `string`                        | `/var/www`  |
| `filesystem.disks.sftp.username`                | `string`                        | `root`      |
| `filesystem.disks.sftp.password`                | `?string`                       | `root`      |
| `filesystem.disks.sftp.privatekey`              | `?string`                       | `null`      |
| `filesystem.disks.sftp.passphrase`              | `?string`                       | `null`      |
| `filesystem.disks.sftp.port`                    | `int`                           | `22`        |
| `filesystem.disks.sftp.useagent`                | `bool`                          | `false`     |
| `filesystem.disks.sftp.timeout`                 | `int`                           | `10`        |
| `filesystem.disks.sftp.maxtries`                | `int`                           | `4`         |
| `filesystem.disks.sftp.fingerprint`             | `string`, `string[]`, or `null` | `null`      |
| `filesystem.disks.sftp.connectivity`            | `ConnectivityChecker` or `null` | `null`      |
| `filesystem.disks.sftp.permission.file.public`  | `int`                           | `0644`      |
| `filesystem.disks.sftp.permission.file.private` | `int`                           | `0600`      |
| `filesystem.disks.sftp.permission.dir.public`   | `int`                           | `0755`      |
| `filesystem.disks.sftp.permission.dir.private`  | `int`                           | `0700`      |

Always verify the server fingerprint in production. Obtain it through a trusted channel and use the exact format expected by Flysystem's phpseclib connection provider. Omitting it allows the client to connect without authenticating the server identity.

### Amazon S3

The bucket and prefix are required configuration values. The AWS SDK can obtain credentials from its standard credential provider chain, so credentials do not need to be stored in the filesystem configuration.

```php
use Aws\S3\S3Client;
use League\Flysystem\Visibility;
use Qubus\Config\Collection;
use Qubus\FileSystem\Adapter\AwsS3FlysystemAdapter;
use Qubus\FileSystem\FileSystem;

$client = new S3Client([
    'version' => 'latest',
    'region' => 'us-west-2',
]);

$config = new Collection([]);
$config->setConfigKey('filesystem', [
    'disks' => [
        'awsS3' => [
            'bucket' => 'example-bucket',
            'prefix' => 'application/uploads',
            'visibility' => Visibility::PRIVATE,
        ],
    ],
]);

$filesystem = new FileSystem(new AwsS3FlysystemAdapter($client, $config));
```

| Configuration key                   | Type     | Default                          |
|-------------------------------------|----------|----------------------------------|
| `filesystem.disks.awsS3.bucket`     | `string` | Required                         |
| `filesystem.disks.awsS3.prefix`     | `string` | Required; use `''` for no prefix |
| `filesystem.disks.awsS3.visibility` | `string` | `public`                         |

## Flysystem operations

`FileSystem` extends Flysystem's `Filesystem`, so the standard Flysystem API is available.

### Write, read, and check files

```php
use League\Flysystem\Visibility;

$filesystem->write('reports/summary.txt', 'Report contents', [
    'visibility' => Visibility::PRIVATE,
]);

$contents = $filesystem->read('reports/summary.txt');

$fileExists = $filesystem->fileExists('reports/summary.txt');
$directoryExists = $filesystem->directoryExists('reports');
$anythingExists = $filesystem->has('reports/summary.txt');
```

### Stream large files

```php
$stream = fopen(__DIR__ . '/large-export.csv', 'rb');

if ($stream === false) {
    throw new RuntimeException('Could not open the export.');
}

try {
    $filesystem->writeStream('exports/large-export.csv', $stream);
} finally {
    fclose($stream);
}

$download = $filesystem->readStream('exports/large-export.csv');

if (is_resource($download)) {
    try {
        // Consume the stream here.
    } finally {
        fclose($download);
    }
}
```

### List a directory

```php
foreach ($filesystem->listContents('reports', deep: true) as $attributes) {
    echo $attributes->path() . PHP_EOL;

    if ($attributes->isFile()) {
        echo 'Size: ' . $attributes->fileSize() . PHP_EOL;
    }
}
```

### Copy, move, and delete

```php
$filesystem->copy('reports/summary.txt', 'archive/summary.txt');
$filesystem->move('archive/summary.txt', 'archive/final-summary.txt');
$filesystem->delete('reports/summary.txt');
$filesystem->deleteDirectory('archive');
```

### Metadata and visibility

```php
use League\Flysystem\Visibility;

$filesystem->setVisibility('documents/private.txt', Visibility::PRIVATE);

$visibility = $filesystem->visibility('documents/private.txt');
$mimeType = $filesystem->mimeType('documents/private.txt');
$size = $filesystem->fileSize('documents/private.txt');
$lastModified = $filesystem->lastModified('documents/private.txt');
```

## Native filesystem helpers

The methods in this section operate on the host filesystem directly. They do not use the configured Flysystem adapter or its root. Pass full or intentionally relative local paths, and never pass untrusted user input without validation.

### Read and write local contents

```php
$contents = $filesystem->getContents(__DIR__ . '/data/input.txt');

if ($contents === false) {
    throw new RuntimeException('The input could not be read.');
}

$bytes = $filesystem->putContents(
    path: __DIR__ . '/data/output.txt',
    contents: $contents,
    lock: true,
);

if ($bytes === false) {
    throw new RuntimeException('The output could not be written.');
}
```

`getContents()` also accepts stream-wrapper URLs. It returns an empty string for a successfully read empty resource and `false` on failure. Only pass trusted URLs, because retrieving an attacker-controlled URL can cause server-side request forgery.

### Create, inspect, and remove directories

```php
$path = __DIR__ . '/runtime/cache';

$filesystem->mkdir($path, permissions: 0755, recursive: true);

if ($filesystem->exists($path)) {
    $directories = $filesystem->directoryListing($path); // Directories only.
    $files = $filesystem->directoryListing($path, 'files');
}

$filesystem->rmdir($path); // Recursively removes the directory and its contents.
```

`rmdir()` unlinks symbolic links instead of following them and refuses to remove a filesystem root. Recursive deletion is irreversible, so resolve and validate the target before calling it.

Use `exists($path, false)` when absence should return `false` rather than throw `NotFoundException`:

```php
if (! $filesystem->exists($path, throw: false)) {
    // The local path does not exist.
}
```

`directoryListing($path)` returns directory names, while `directoryListing($path, 'files')` returns file names. It is distinct from Flysystem's adapter-backed `listContents()` method.

### Modify an existing local file

```php
$log = __DIR__ . '/runtime/application.log';

$filesystem->prepend($log, "Log started\n");
$filesystem->append($log, "Log entry\n");
$filesystem->update($log, "Replacement contents\n");
```

These methods return `false` when the path is not an existing regular file. Mutations use an exclusive file lock.

### Normalize paths and trailing slashes

```php
$normalized = $filesystem->normalizePath('documents/./drafts/../final.txt');
// documents/final.txt

$withoutSlash = $filesystem->removeTrailingSlash('documents///');
// documents

$withSlash = $filesystem->addTrailingSlash('documents\\');
// documents/
```

Flysystem path normalization rejects traversal above the storage root and control characters in paths.

## Error handling

Flysystem operations throw exceptions implementing `League\Flysystem\FilesystemException`. More specific exceptions, such as `UnableToReadFile` and `UnableToWriteFile`, are available when the application needs operation-specific handling.

```php
use League\Flysystem\FilesystemException;

try {
    $filesystem->write('documents/example.txt', 'contents');
} catch (FilesystemException $exception) {
    // Log, report, or translate the storage failure.
}
```

The native helpers may throw exceptions from `qubus/exception`:

- `NotFoundException` when a required local path or listing cannot be found.
- `DirectoryNotWritableException` when a local directory cannot be created.
- `Qubus\Exception\Exception` for an empty directory path.
- `TypeException` when adapter configuration has the wrong value type.
- `InvalidArgumentException` for invalid listing modes or attempts to recursively remove a filesystem root.

## Security guidance

- Store credentials in environment variables or a secret manager, not in source control.
- Supply explicit FTP and SFTP credentials in production. The built-in connection defaults exist for backwards compatibility only.
- Prefer SFTP or properly configured FTPS over unencrypted FTP.
- Verify SFTP host fingerprints.
- Keep S3 buckets private unless public access is intentional and use the narrowest practical IAM permissions.
- Treat adapter-backed paths and native local paths as separate trust boundaries.
- Do not pass untrusted URLs to `getContents()` or untrusted paths to native helpers.

## Configuration

The filesystem configuration file can be found in at `config/filesystem.php`. The configuration file is only set up for 
one local filesystem and Amazon S3.

## Disks

Here is a look at the filesystem config showing the path for each disk: local, public, cache, media, sessions, cookies, 
view, logs, and S3.

    <?php
    
    declare(strict_types=1);
    
    use function Codefy\Framework\Helpers\storage_path;
    use function Qubus\Config\Helpers\env;
    
    return [
        /*
        |--------------------------------------------------------------------------
        | Filesystem disks. You may add as many filesystem disks as you need.
        |
        | Supported Drivers: "local", "ftp", "sftp", "s3"
        |--------------------------------------------------------------------------
        */
        'disks' => [
            /*
            |--------------------------------------------------------------------------
            | Default local disk.
            |--------------------------------------------------------------------------
            */
            'local' => [
                'root' => storage_path(),
                'visibility' => \League\Flysystem\Visibility::PUBLIC,
                'permission' => [
                    'file' => [
                        'public'  => 0644,
                        'private' => 0604,
                    ],
                    'dir'  => [
                        'public'  => 0755,
                        'private' => 7604,
                    ],
                ],
            ],
    
            /*
            |--------------------------------------------------------------------------
            | Public disk.
            |--------------------------------------------------------------------------
            */
            'public' => [
                'root' => storage_path(path: 'app/public'),
                'visibility' => \League\Flysystem\Visibility::PUBLIC,
                'permission' => [
                    'file' => [
                        'public'  => 0644,
                        'private' => 0604,
                    ],
                    'dir'  => [
                        'public'  => 0755,
                        'private' => 7604,
                    ],
                ],
            ],
    
            /*
            |--------------------------------------------------------------------------
            | Cache disk.
            |--------------------------------------------------------------------------
            */
            'cache' => [
                'root' => storage_path(path: 'framework/cache'),
                'visibility' => \League\Flysystem\Visibility::PRIVATE,
                'permission' => [
                    'file' => [
                        'public'  => 0644,
                        'private' => 0604,
                    ],
                    'dir'  => [
                        'public'  => 0755,
                        'private' => 7604,
                    ],
                ],
            ],
    
            /*
            |--------------------------------------------------------------------------
            | Media disk.
            |--------------------------------------------------------------------------
            */
            'media' => [
                'root' => storage_path(path: 'framework/media'),
                'visibility' => \League\Flysystem\Visibility::PUBLIC,
                'permission' => [
                    'file' => [
                        'public'  => 0644,
                        'private' => 0604,
                    ],
                    'dir'  => [
                        'public'  => 0755,
                        'private' => 7604,
                    ],
                ],
            ],
    
            /*
            |--------------------------------------------------------------------------
            | Session disk.
            |--------------------------------------------------------------------------
            */
            'sessions' => [
                'root' => storage_path(path: 'framework/sessions'),
                'visibility' => \League\Flysystem\Visibility::PRIVATE,
                'permission' => [
                    'file' => [
                        'public'  => 0644,
                        'private' => 0604,
                    ],
                    'dir'  => [
                        'public'  => 0755,
                        'private' => 7604,
                    ],
                ],
            ],
    
            /*
            |--------------------------------------------------------------------------
            | Session disk.
            |--------------------------------------------------------------------------
            */
            'cookies' => [
                'root' => storage_path(path: 'framework/cookies'),
                'visibility' => \League\Flysystem\Visibility::PRIVATE,
                'permission' => [
                    'file' => [
                        'public'  => 0644,
                        'private' => 0604,
                    ],
                    'dir'  => [
                        'public'  => 0755,
                        'private' => 7604,
                    ],
                ],
            ],
    
            /*
            |--------------------------------------------------------------------------
            | View disk.
            |--------------------------------------------------------------------------
            */
            'views' => [
                'root' => storage_path(path: 'framework/views'),
                'visibility' => \League\Flysystem\Visibility::PRIVATE,
                'permission' => [
                    'file' => [
                        'public'  => 0644,
                        'private' => 0604,
                    ],
                    'dir'  => [
                        'public'  => 0755,
                        'private' => 7604,
                    ],
                ],
            ],
    
            /*
            |--------------------------------------------------------------------------
            | Log disk.
            |--------------------------------------------------------------------------
            */
            'logs' => [
                'root' => storage_path(path: 'logs'),
                'visibility' => \League\Flysystem\Visibility::PRIVATE,
                'permission' => [
                    'file' => [
                        'public'  => 0644,
                        'private' => 0604,
                    ],
                    'dir'  => [
                        'public'  => 0755,
                        'private' => 7604,
                    ],
                ],
            ],
    
            /*
            |--------------------------------------------------------------------------
            | Amazon S3
            |--------------------------------------------------------------------------
            */
            'awsS3' => [
                'driver' => 's3',
                'key' => env(key: 'AWS_ACCESS_KEY_ID'),
                'secret' => env(key: 'AWS_SECRET_ACCESS_KEY'),
                'region' => env(key: 'AWS_DEFAULT_REGION'),
                'bucket' => env(key: 'AWS_BUCKET'),
                'url' => env(key: 'AWS_URL'),
                'endpoint' => env(key: 'AWS_ENDPOINT'),
                'prefix' => '',
                'visibility' => \League\Flysystem\Visibility::PRIVATE,
            ],
        ],
        /*
        |--------------------------------------------------------------------------
        | Config for Local FileSystem.
        |--------------------------------------------------------------------------
        */
        'local' => [
            /*
            |--------------------------------------------------------------------------
            | Set the root directory.
            |--------------------------------------------------------------------------
            */
            'root' => storage_path(),
            /*
            |--------------------------------------------------------------------------
            | Set the visibility for files and directories.
            |--------------------------------------------------------------------------
            */
            'visibility' => \League\Flysystem\Visibility::PUBLIC,
            'permission' => [
                'file' => [
                    'public'  => 0644,
                    'private' => 0604,
                ],
                'dir'  => [
                    'public'  => 0755,
                    'private' => 7604,
                ],
            ],
        ],
    ];
