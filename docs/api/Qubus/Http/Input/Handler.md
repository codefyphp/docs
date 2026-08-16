# Handler

***

* Full name: `\Qubus\Http\Input\Handler`

## Properties

### get

```php
protected array $get
```

***

### post

```php
protected array $post
```

***

### file

```php
protected array $file
```

***

### originalPost

Original post variables.

```php
public array $originalPost
```

***

### originalParams

Original get/params variables.

```php
public array $originalParams
```

***

### originalFile

Get original file variables.

```php
protected array $originalFile
```

***

### request

```php
public \Qubus\Http\Request $request
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Http\Request $request): mixed
```

**Parameters:**

| Parameter  | Type                    | Description |
|------------|-------------------------|-------------|
| `$request` | **\Qubus\Http\Request** |             |

***

### parseInputs

Parse input values.

```php
public parseInputs(): void
```

***

### parseFiles

```php
public parseFiles(array $files, string|null $parentKey = null): array
```

**Parameters:**

| Parameter    | Type             | Description                                       |
|--------------|------------------|---------------------------------------------------|
| `$files`     | **array**        | Array with files to parse.                        |
| `$parentKey` | **string\|null** | Key from parent (used when parsing nested array). |

***

### rearrangeFile

Rearrange multidimensional file object created by PHP.

```php
protected rearrangeFile(array $values, array& $index, array|null $original = null): array|null
```

**Parameters:**

| Parameter   | Type            | Description |
|-------------|-----------------|-------------|
| `$values`   | **array**       |             |
| `$index`    | **array**       |             |
| `$original` | **array\|null** |             |

***

### parseInputItem

Parse input item from array.

```php
protected parseInputItem(array $array): array
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$array`  | **array** |             |

***

### find

Find input object.

```php
public find(string $index, array $methods): string|\Qubus\Http\Input\Input|array|\Qubus\Http\Input\File|null
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$index`   | **string** |             |
| `$methods` | **array**  |             |

***

### getValueFromArray

```php
protected getValueFromArray(array $array): array
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$array`  | **array** |             |

***

### value

Get input element value matching index.

```php
public value(string $index, string|null|mixed $defaultValue = null, array $methods): array|string|null
```

**Parameters:**

| Parameter       | Type                    | Description |
|-----------------|-------------------------|-------------|
| `$index`        | **string**              |             |
| `$defaultValue` | **string\|null\|mixed** |             |
| `$methods`      | **array**               |             |

***

### exists

Check if an input item exist. If an array is an
$index parameter the method returns true if all
elements exist.

```php
public exists(string|array $index, array $methods): bool
```

**Parameters:**

| Parameter  | Type              | Description |
|------------|-------------------|-------------|
| `$index`   | **string\|array** |             |
| `$methods` | **array**         |             |

***

### post

Find post-value by index or return default value.

```php
public post(string $index, string|null $defaultValue = null): \Qubus\Http\Input\Input|array|string|null
```

**Parameters:**

| Parameter       | Type             | Description |
|-----------------|------------------|-------------|
| `$index`        | **string**       |             |
| `$defaultValue` | **string\|null** |             |

***

### file

Find file by index or return default value.

```php
public file(string $index, string|null $defaultValue = null): \Qubus\Http\Input\File|array|string|null
```

**Parameters:**

| Parameter       | Type             | Description |
|-----------------|------------------|-------------|
| `$index`        | **string**       |             |
| `$defaultValue` | **string\|null** |             |

***

### get

Find parameter/query-string by index or return default value.

```php
public get(string $index, string|null $defaultValue = null): \Qubus\Http\Input\Input|array|string|null
```

**Parameters:**

| Parameter       | Type             | Description |
|-----------------|------------------|-------------|
| `$index`        | **string**       |             |
| `$defaultValue` | **string\|null** |             |

***

### all

Get all get/post items.

```php
public all(array $filter = []): array
```

**Parameters:**

| Parameter | Type      | Description                |
|-----------|-----------|----------------------------|
| `$filter` | **array** | Only take items in filter. |

***

### addGet

Add GET parameter.

```php
public addGet(string $key, \Qubus\Http\Input\Input $input): void
```

**Parameters:**

| Parameter | Type                        | Description |
|-----------|-----------------------------|-------------|
| `$key`    | **string**                  |             |
| `$input`  | **\Qubus\Http\Input\Input** |             |

***

### addPost

Add POST parameter.

```php
public addPost(string $key, \Qubus\Http\Input\Input $input): void
```

**Parameters:**

| Parameter | Type                        | Description |
|-----------|-----------------------------|-------------|
| `$key`    | **string**                  |             |
| `$input`  | **\Qubus\Http\Input\Input** |             |

***

### addFile

Add FILE parameter.

```php
public addFile(string $key, \Qubus\Http\Input\File $file): void
```

**Parameters:**

| Parameter | Type                       | Description |
|-----------|----------------------------|-------------|
| `$key`    | **string**                 |             |
| `$file`   | **\Qubus\Http\Input\File** |             |

***

### withOriginalPost

Set original post variables.

```php
public withOriginalPost(array $post): static
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$post`   | **array** |             |

**Return Value:**

$this

***

### withOriginalParams

Set original get-variables.

```php
public withOriginalParams(array $params): static
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$params` | **array** |             |

**Return Value:**

$this

***

### withOriginalFile

Set original file posts variables.

```php
public withOriginalFile(array $file): static
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$file`   | **array** |             |

**Return Value:**

$this

***
