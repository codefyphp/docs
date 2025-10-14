***

# FileSystem





* Full name: `\Qubus\FileSystem\FileSystem`
* Parent class: [`Filesystem`](../../League/Flysystem/Filesystem.md)
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### adapter



```php
private \League\Flysystem\FilesystemAdapter $adapter
```






***

### config



```php
private array $config
```






***

### pathNormalizer



```php
private ?\League\Flysystem\PathNormalizer $pathNormalizer
```






***

## Methods


### __construct



```php
public __construct(\League\Flysystem\FilesystemAdapter $adapter, array $configArray = [], ?\League\Flysystem\PathNormalizer $pathNormalizer = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$adapter` | **\League\Flysystem\FilesystemAdapter** |  |
| `$configArray` | **array** |  |
| `$pathNormalizer` | **?\League\Flysystem\PathNormalizer** |  |





***

### getContents

Custom function to use curl, fopen, or use file_get_contents
if curl is not available.

```php
public getContents(string $filename, bool $useIncludePath = false, bool $context = true): string|bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$filename` | **string** | Resource to read. |
| `$useIncludePath` | **bool** | Whether to use include path. |
| `$context` | **bool** | Whether to use a context resource. |





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

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **string** | Path to be created. |
| `$permissions` | **int** | Permission to set for directory. |
| `$recursive` | **bool** | Whether to allow the creation of nested directories. |


**Return Value:**

True if the directory was created.



**Throws:**
<p>If path is not writable, or lacks permission to mkdir.</p>

- [`DirectoryNotWritableException`](../Exception/IO/FileSystem/DirectoryNotWritableException.md)
<p>If path is invalid.</p>

- [`Exception`](../Exception/Exception.md)



***

### rmdir

Removes directory recursively along with any files.

```php
public rmdir(string $dir): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$dir` | **string** | Directory that should be removed. |





***

### exists

Checks whether a file or directory exists.

```php
public exists(string $filename, bool $throw = true): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$filename` | **string** | Path to the file or directory. |
| `$throw` | **bool** | Determines whether to do a simple check or throw an exception.<br />Default: true. |


**Return Value:**

True if the file or directory specified by $filename exists;
false otherwise if $throw is set to false.



**Throws:**
<p>If file does not exist.</p>

- [`NotFoundException`](../Exception/Http/Client/NotFoundException.md)



***

### directoryListing

Get an array that represents directory tree.

```php
public directoryListing(string $dir, string $include = &#039;dirs&#039;): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$dir` | **string** | Directory path. |
| `$include` | **string** | Include sub directories. Default: dirs. Option: files. |





***

### normalizePath

Normalize a filesystem path.

```php
public normalizePath(string $path): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **string** | Path to normalize. |


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

| Parameter | Type | Description |
|-----------|------|-------------|
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

| Parameter | Type | Description |
|-----------|------|-------------|
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

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **string** |  |
| `$data` | **string** |  |




**Throws:**

- [`NotFoundException`](../Exception/Http/Client/NotFoundException.md)



***

### append

Appends data to a file.

```php
public append(string $path, string $data): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **string** |  |
| `$data` | **string** |  |




**Throws:**

- [`NotFoundException`](../Exception/Http/Client/NotFoundException.md)



***

### update

Updates a file.

```php
public update(string $path, string $data): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **string** |  |
| `$data` | **string** |  |




**Throws:**

- [`NotFoundException`](../Exception/Http/Client/NotFoundException.md)



***


***
> Automatically generated on 2025-10-13
