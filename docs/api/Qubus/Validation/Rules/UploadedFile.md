# UploadedFile

***

* Full name: `\Qubus\Validation\Rules\UploadedFile`
* Parent class: [`\Qubus\Validation\Rule`](../Rule.md)
* This class implements:
  [`\Qubus\Validation\Rules\Interfaces\BeforeValidate`](./Interfaces/BeforeValidate.md)

## Properties

### message

```php
protected string $message
```

***

### maxSize

```php
protected string|int|null $maxSize
```

***

### minSize

```php
protected string|int|null $minSize
```

***

### allowedTypes

```php
protected array $allowedTypes
```

***

## Methods

### fillParameters

Given $params and assign $this->params.

```php
public fillParameters(array $params): self
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$params` | **array** |             |

***

### maxSize

Given $size and set the max size

```php
public maxSize(int|string|null $size = null): self
```

**Parameters:**

| Parameter | Type                  | Description |
|-----------|-----------------------|-------------|
| `$size`   | **int\|string\|null** |             |

***

### minSize

Given $size and set the min size

```php
public minSize(int|string|null $size = null): self
```

**Parameters:**

| Parameter | Type                  | Description |
|-----------|-----------------------|-------------|
| `$size`   | **int\|string\|null** |             |

***

### sizeBetween

Given $min and $max then set the range size

```php
public sizeBetween(int|string|null $min = null, int|string|null $max = null): self
```

**Parameters:**

| Parameter | Type                  | Description |
|-----------|-----------------------|-------------|
| `$min`    | **int\|string\|null** |             |
| `$max`    | **int\|string\|null** |             |

***

### fileTypes

Given $types and assign $this->params

```php
public fileTypes(mixed $types): self
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$types`  | **mixed** |             |

***

### beforeValidate

Before validate hook.

```php
public beforeValidate(): void
```

***

### check

Check the $value is valid.

```php
public check(mixed $value): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

## Inherited methods

### check

```php
public check(mixed $value): bool
```

* This method is **abstract**.
**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### setValidation

Set Validation class instance

```php
public setValidation(\Qubus\Validation\Validation $validation): void
```

**Parameters:**

| Parameter     | Type                             | Description |
|---------------|----------------------------------|-------------|
| `$validation` | **\Qubus\Validation\Validation** |             |

***

### setKey

Set key

```php
public setKey(string $key): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### getKey

Get key

```php
public getKey(): string
```

***

### setAttribute

Set attribute

```php
public setAttribute(\Qubus\Validation\Attribute $attribute): void
```

**Parameters:**

| Parameter    | Type                            | Description |
|--------------|---------------------------------|-------------|
| `$attribute` | **\Qubus\Validation\Attribute** |             |

***

### getAttribute

Get attribute

```php
public getAttribute(): \Qubus\Validation\Attribute|null
```

***

### getParameters

Get parameters

```php
public getParameters(): array
```

***

### setParameters

Set params

```php
public setParameters(array $params): \Qubus\Validation\Rule
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$params` | **array** |             |

***

### setParameter

Set parameters

```php
public setParameter(string $key, mixed $value): \Qubus\Validation\Rule
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |
| `$value`  | **mixed**  |             |

***

### fillParameters

Fill $params to $this->params

```php
public fillParameters(array $params): \Qubus\Validation\Rule
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$params` | **array** |             |

***

### parameter

Get parameter from given $key, return null if it not exists

```php
public parameter(string $key): mixed
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### setParameterText

Set parameter text that can be displayed in error message using ':param_key'

```php
public setParameterText(string $key, string $text): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |
| `$text`   | **string** |             |

***

### getParametersTexts

Get $paramsTexts

```php
public getParametersTexts(): array
```

***

### isImplicit

Check whether this rule is implicit

```php
public isImplicit(): bool
```

***

### message

Just alias of setMessage

```php
public message(string $message): \Qubus\Validation\Rule
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$message` | **string** |             |

***

### setMessage

Set message

```php
public setMessage(string $message): \Qubus\Validation\Rule
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$message` | **string** |             |

***

### getMessage

Get message

```php
public getMessage(): string
```

***

### requireParameters

Check given $params must exist.

```php
protected requireParameters(array $params): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$params` | **array** |             |

**Throws:**

- [`MissingRequiredParameterException`](../MissingRequiredParameterException.md)

***

### getValueSize

Get size (int) value from given $value

```php
protected getValueSize(mixed $value): float|false
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### getBytesSize

Given $size and get the bytes

```php
protected getBytesSize(mixed $size): float
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$size`   | **mixed** |             |

**Throws:**

- [`InvalidArgumentException`](../../../InvalidArgumentException.md)

***

### isUploadedFileValue

Check whether value is from $_FILES

```php
public isUploadedFileValue(mixed $value): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### isValueFromUploadedFiles

Check whether value is from $_FILES

```php
public isValueFromUploadedFiles(mixed $value): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### isUploadedFile

Check the $value is uploaded file

```php
public isUploadedFile(mixed $value): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### resolveUploadedFileValue

Resolve uploaded file value

```php
public resolveUploadedFileValue(mixed $value): array|null
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***
