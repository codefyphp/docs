***

# FileAdapter





* Full name: `\Qubus\View\Adapter\FileAdapter`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Qubus\View\Adapter\Adapter`](./Adapter.md)
* This class is a **Final class**



## Properties


### source



```php
private string|array $source
```






***

## Methods


### __construct



```php
public __construct(string|array $source): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$source` | **string&#124;array** |  |





***

### isReadable



```php
public isReadable(string $path): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **string** |  |





***

### lastModified



```php
public lastModified(string $path): int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **string** |  |





***

### getContents



```php
public getContents(string $path): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **string** |  |





***

### putContents



```php
public putContents(string $path, string $contents): int|bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **string** |  |
| `$contents` | **string** |  |





***

### getStreamUrl



```php
public getStreamUrl(string $path): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **string** |  |





***


***
> Automatically generated on 2025-10-13
