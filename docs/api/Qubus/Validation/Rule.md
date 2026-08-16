# Rule

***

* Full name: `\Qubus\Validation\Rule`
* This class is an **Abstract class**

## Properties

### key

```php
protected ?string $key
```

***

### attribute

```php
protected ?\Qubus\Validation\Attribute $attribute
```

***

### validation

```php
protected ?\Qubus\Validation\Validation $validation
```

***

### implicit

```php
protected bool $implicit
```

***

### params

```php
protected array $params
```

***

### paramsTexts

```php
protected array $paramsTexts
```

***

### fillableParams

```php
protected array $fillableParams
```

***

### message

```php
protected string $message
```

***

## Methods

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

- [`MissingRequiredParameterException`](./MissingRequiredParameterException.md)

***
