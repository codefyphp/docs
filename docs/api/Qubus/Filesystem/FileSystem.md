# FileSystem

***

* Full name: `\Qubus\FileSystem\FileSystem`
* Parent class: [`Filesystem`](../../League/Flysystem/Filesystem.md)
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Properties

### pathNormalizer

```php
private \League\Flysystem\PathNormalizer $pathNormalizer
```

***

## Methods

### __construct

```php
public __construct(\League\Flysystem\FilesystemAdapter $adapter, array<string,mixed> $configArray = [], ?\League\Flysystem\PathNormalizer $pathNormalizer = null): mixed
```

**Parameters:**

| Parameter         | Type                                    | Description |
|-------------------|-----------------------------------------|-------------|
| `$adapter`        | **\League\Flysystem\FilesystemAdapter** |             |
| `$configArray`    | **array<string,mixed>**                 |             |
| `$pathNormalizer` | **?\League\Flysystem\PathNormalizer**   |             |

***

### getContents

Custom function to use curl, fopen, or use file_get_contents
if curl is not available.

```php
public getContents(string $filename, bool $useIncludePath = false, bool $context = true): string|bool
```

**Parameters:**

| Parameter         | Type       | Description                        |
|-------------------|------------|------------------------------------|
| `$filename`       | **string** | Resource to read.                  |
| `$useIncludePath` | **bool**   | Whether to use include path.       |
| `$context`        | **bool**   | Whether to use a context resource. |

***

### putContents

Write the contents of a file.

```php
public putContents(string $path, string $contents, bool $lock = false): int|bool
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$path`     | **string** |             |
| `$contents` | **string** |             |
| `$lock`     | **bool**   |             |

***

### mkdir

Custom make directory function.

```php
public mkdir(string $path, int $permissions = 0755, bool $recursive = true): bool
```

This function will check if the path is an existing directory,
if not, then it will be created with set permissions and also created
recursively if needed.

**Parameters:**

| Parameter      | Type       | Description                                          |
|----------------|------------|------------------------------------------------------|
| `$path`        | **string** | Path to be created.                                  |
| `$permissions` | **int**    | Permission to set for directory.                     |
| `$recursive`   | **bool**   | Whether to allow the creation of nested directories. |

**Return Value:**

True if the directory was created.

**Throws:**

If path is not writable, or lacks permission to mkdir.
- [`DirectoryNotWritableException`](../Exception/IO/FileSystem/DirectoryNotWritableException.md)
If path is invalid.
- [`Exception`](../Exception/Exception.md)

***

### rmdir

Removes directory recursively along with any files.

```php
public rmdir(string $dir): void
```

**Parameters:**

| Parameter | Type       | Description                       |
|-----------|------------|-----------------------------------|
| `$dir`    | **string** | Directory that should be removed. |

**Throws:**

If the path resolves to a filesystem root.
- [`InvalidArgumentException`](../../InvalidArgumentException.md)

***

### exists

Checks whether a file or directory exists.

```php
public exists(string $filename, bool $throw = true): bool
```

**Parameters:**

| Parameter   | Type       | Description                                                                   |
|-------------|------------|-------------------------------------------------------------------------------|
| `$filename` | **string** | Path to the file or directory.                                                |
| `$throw`    | **bool**   | Determines whether to do a simple check or throw an exception.
Default: true. |

**Return Value:**

True if the file or directory specified by $filename exists;
false otherwise if $throw is set to false.

**Throws:**

If file does not exist.
- [`NotFoundException`](../Exception/Http/Client/NotFoundException.md)

***

### directoryListing

Get an array that represents the directory tree.

```php
public directoryListing(string $dir, string $include = 'dirs'): list<string>
```

**Parameters:**

| Parameter  | Type       | Description                                            |
|------------|------------|--------------------------------------------------------|
| `$dir`     | **string** | Directory path.                                        |
| `$include` | **string** | Include sub directories. Default: dirs. Option: files. |

**Throws:**

- [`NotFoundException`](../Exception/Http/Client/NotFoundException.md)

***

### normalizePath

Normalize a filesystem path.

```php
public normalizePath(string $path): string
```

**Parameters:**

| Parameter | Type       | Description        |
|-----------|------------|--------------------|
| `$path`   | **string** | Path to normalize. |

**Return Value:**

Normalized path.

***

### removeTrailingSlash

Removes trailing forward slashes and backslashes if they exist.

```php
public removeTrailingSlash(string $string): string
```

The primary use of this is for paths and thus should be used for paths. It is
not restricted to paths and offers no specific path support.

**Parameters:**

| Parameter | Type       | Description                               |
|-----------|------------|-------------------------------------------|
| `$string` | **string** | What to remove the trailing slashes from. |

**Return Value:**

String without the trailing slashes.

***

### addTrailingSlash

Appends a trailing slash.

```php
public addTrailingSlash(string $string): string
```

Will remove trailing forward and backslashes if it exists already before adding
a trailing forward slash. This prevents double slashing a string or path.

The primary use of this is for paths and thus should be used for paths. It is
not restricted to paths and offers no specific path support.

**Parameters:**

| Parameter | Type       | Description                        |
|-----------|------------|------------------------------------|
| `$string` | **string** | What to add the trailing slash to. |

**Return Value:**

String with trailing slash added.

***

### prepend

Prepends data to a file.

```php
public prepend(string $path, string $data): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$path`   | **string** |             |
| `$data`   | **string** |             |

***

### append

Appends data to a file.

```php
public append(string $path, string $data): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$path`   | **string** |             |
| `$data`   | **string** |             |

***

### update

Updates a file.

```php
public update(string $path, string $data): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$path`   | **string** |             |
| `$data`   | **string** |             |

***

### writeToExistingFile

```php
private writeToExistingFile(string $path, string $data, bool $prepend = false, bool $append = false): bool
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$path`    | **string** |             |
| `$data`    | **string** |             |
| `$prepend` | **bool**   |             |
| `$append`  | **bool**   |             |

***
