# MakeCommandAware

***

* Full name: `\Codefy\Framework\Console\Commands\Traits\MakeCommandAware`
* **Warning:** this trait is **deprecated**. This means that this class will likely be removed in a future version.

## Methods

### resolveResource

```php
private resolveResource(string $resource, mixed $options): void
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$resource` | **string** |             |
| `$options`  | **mixed**  |             |

**Throws:**

- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)
- [`MakeCommandFileAlreadyExistsException`](../../Exceptions/MakeCommandFileAlreadyExistsException.md)
- [`ReflectionException`](../../../../../ReflectionException.md)

***
### resolveClassNameSuffix

```php
private resolveClassNameSuffix(string $classNameSuffix, string $classNamePrefix, mixed|null $options = null): void
```

**Parameters:**

| Parameter          | Type            | Description |
|--------------------|-----------------|-------------|
| `$classNameSuffix` | **string**      |             |
| `$classNamePrefix` | **string**      |             |
| `$options`         | **mixed\|null** |             |

**Throws:**

- [`MakeCommandFileAlreadyExistsException`](../../Exceptions/MakeCommandFileAlreadyExistsException.md)
- [`ReflectionException`](../../../../../ReflectionException.md)
- [`TypeException`](../../../../../Qubus/Exception/Data/TypeException.md)
- [`Exception`](../../../../../Exception.md)

***
### createClassFromStub

Create the class file based on the stub file. Once the file is resolved and have a valid directory path
and the stub content is properly filtered and change to reflect. Then and only then we will
generate the actual usable class file.

```php
public createClassFromStub(string $qualifiedClass, string|null $contentStream = null, string|null $classNameSuffix = null, string|null $flag = null, string|null $qualifiedNamespaces = null): void
```

Note. realpath will return false if the file or directory does not exist.

**Parameters:**

| Parameter              | Type             | Description                                      |
|------------------------|------------------|--------------------------------------------------|
| `$qualifiedClass`      | **string**       |                                                  |
| `$contentStream`       | **string\|null** |                                                  |
| `$classNameSuffix`     | **string\|null** |                                                  |
| `$flag`                | **string\|null** |                                                  |
| `$qualifiedNamespaces` | **string\|null** | - will return the namespace for the stub command |

**Throws:**

- [`MakeCommandFileAlreadyExistsException`](../../Exceptions/MakeCommandFileAlreadyExistsException.md)
- [`Exception`](../../../../../Exception.md)
- [`ReflectionException`](../../../../../ReflectionException.md)

***
### addOptionalDirFlag

console command option flag. Use --dir={directory_name} to add a directory to the end
of the filepath to create a subdirectory within a main directory

```php
private addOptionalDirFlag(string $flag): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$flag`   | **string** |             |

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

| Parameter          | Type       | Description |
|--------------------|------------|-------------|
| `$classNameSuffix` | **string** |             |

***
### resolveStubContentPlaceholders

```php
private resolveStubContentPlaceholders(string $file, string $classNameSuffix, string $classNamePrefix): array|bool
```

**Parameters:**

| Parameter          | Type       | Description |
|--------------------|------------|-------------|
| `$file`            | **string** |             |
| `$classNameSuffix` | **string** |             |
| `$classNamePrefix` | **string** |             |

***
### resolveModelDependency

Resolve the model dependency by specifying which Stubs class will require a model.

```php
private resolveModelDependency(string $classNamePrefix, string $classNameSuffix): array|bool
```

**Parameters:**

| Parameter          | Type       | Description |
|--------------------|------------|-------------|
| `$classNamePrefix` | **string** |             |
| `$classNameSuffix` | **string** |             |

***
