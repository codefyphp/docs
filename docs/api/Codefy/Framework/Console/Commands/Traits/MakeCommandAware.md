***

# MakeCommandAware





* Full name: `\Codefy\Framework\Console\Commands\Traits\MakeCommandAware`




## Methods


### resolveResource



```php
private resolveResource(string $resource, mixed $options): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$resource` | **string** |  |
| `$options` | **mixed** |  |




**Throws:**

- [`\Qubus\Exception\Data\TypeException|\Codefy\Framework\Console\Exceptions\MakeCommandFileAlreadyExistsException`](../../../../../Qubus/Exception/Data/TypeException|/Codefy/Framework/Console/Exceptions/MakeCommandFileAlreadyExistsException.md)



***

### resolveClassNameSuffix



```php
private resolveClassNameSuffix(string $classNameSuffix, string $classNamePrefix, mixed|null $options = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$classNameSuffix` | **string** |  |
| `$classNamePrefix` | **string** |  |
| `$options` | **mixed&#124;null** |  |




**Throws:**

- [`MakeCommandFileAlreadyExistsException`](../../Exceptions/MakeCommandFileAlreadyExistsException.md)

- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)



***

### createClassFromStub

Create the class file based on the stub file. Once the file is resolved and have a valid directory path
and the stub content is properly filtered and change to reflect. Then and only then we will
generate the actual usable class file.

```php
public createClassFromStub(string $qualifiedClass, string|null $contentStream = null, string|null $classNameSuffix = null, mixed|null $options = null, string|null $qualifiedNamespaces = null): void
```

Note. realpath will return false if the file or directory does not exist.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$qualifiedClass` | **string** |  |
| `$contentStream` | **string&#124;null** |  |
| `$classNameSuffix` | **string&#124;null** |  |
| `$options` | **mixed&#124;null** |  |
| `$qualifiedNamespaces` | **string&#124;null** | - will return the namespace for the stub command |




**Throws:**

- [`MakeCommandFileAlreadyExistsException`](../../Exceptions/MakeCommandFileAlreadyExistsException.md)

- [`Exception`](../../../../../Qubus/Exception/Exception.md)

- [`ReflectionException`](../../../../../ReflectionException.md)



***

### addOptionalDirFlag

console command option flag. Use --dir={directory_name} to add a directory to the end
of the filepath to create a subdirectory within a main directory

```php
private addOptionalDirFlag(mixed $options): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$options` | **mixed** |  |





***

### getStubFiles

Uses the php glob to retrieve all stub files form the relevant directory. Which will return
an array of files within the specified directory with the [.stub] extension.

```php
private getStubFiles(string $classNameSuffix): string|false
```

We then iterate over that array and uses php str_contain function to match a file from
the array with the classNameSuffix. When we have a match then return the matching file string.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$classNameSuffix` | **string** |  |





***

### resolveStubContentPlaceholders



```php
private resolveStubContentPlaceholders(string $file, string $classNameSuffix, string $classNamePrefix): array|bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$file` | **string** |  |
| `$classNameSuffix` | **string** |  |
| `$classNamePrefix` | **string** |  |





***

### resolveModelDependency

Resolve the model dependency by specifying which Stubs class will require a model.

```php
private resolveModelDependency(string $classNamePrefix, string $classNameSuffix): array|bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$classNamePrefix` | **string** |  |
| `$classNameSuffix` | **string** |  |





***

***
> Automatically generated on 2025-10-13

