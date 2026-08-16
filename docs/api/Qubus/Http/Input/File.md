# File

***

* Full name: `\Qubus\Http\Input\File`
* This class implements:
  [`\Qubus\Http\Input\Item`](./Item.md)

## Properties

### index

```php
public string|int $index
```

***

### name

```php
public string $name
```

***

### filename

```php
public ?string $filename
```

***

### size

```php
public ?int $size
```

***

### type

```php
public ?string $type
```

***

### errors

```php
public int $errors
```

***

### tmpName

```php
public ?string $tmpName
```

***

## Methods

### __construct

```php
public __construct(string|int $index): mixed
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$index`  | **string\|int** |             |

***

### createFromArray

Create from array

```php
public static createFromArray(array $values): static
```

* This method is **static**.
**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$values` | **array** |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)

***

### getIndex

```php
public getIndex(): string
```

***

### setIndex

Set input index

```php
public setIndex(string $index): static
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$index`  | **string** |             |

***

### getSize

```php
public getSize(): int
```

***

### setSize

Set file size

```php
public setSize(int $size): static
```

**Parameters:**

| Parameter | Type    | Description |
|-----------|---------|-------------|
| `$size`   | **int** |             |

***

### getMime

Get mime-type of file

```php
public getMime(): string
```

***

### getType

```php
public getType(): string
```

***

### setType

Set type

```php
public setType(string $type): static
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$type`   | **string** |             |

***

### getExtension

Returns extension without "."

```php
public getExtension(): string
```

***

### getName

Get human friendly name

```php
public getName(): ?string
```

***

### setName

Set human friendly name.

```php
public setName(string $name): static
```

Useful for adding validation etc.

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### setFilename

Set filename

```php
public setFilename(string $name): static
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### getFilename

Get filename

```php
public getFilename(): null|string
```

**Return Value:**

mixed

***

### move

Move the uploaded temporary file to it's new home

```php
public move(string $destination): bool
```

**Parameters:**

| Parameter      | Type       | Description |
|----------------|------------|-------------|
| `$destination` | **string** |             |

***

### getContents

Get file contents

```php
public getContents(): string
```

***

### hasError

Return true if an upload error occurred.

```php
public hasError(): bool
```

***

### getError

Get upload-error code.

```php
public getError(): ?int
```

***

### setError

Set error

```php
public setError(?int $error = null): static
```

**Parameters:**

| Parameter | Type     | Description |
|-----------|----------|-------------|
| `$error`  | **?int** |             |

***

### getTmpName

```php
public getTmpName(): string
```

***

### setTmpName

Set file temp. name

```php
public setTmpName(string $name): static
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***

### __toString

```php
public __toString(): string
```

***

### getValue

```php
public getValue(): ?string
```

***

### setValue

```php
public setValue(string $value): static
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$value`  | **string** |             |

***

### toArray

```php
public toArray(): array
```

***
