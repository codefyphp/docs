# FormDataRequest

***

* Full name: `\Codefy\Framework\Http\Request\FormDataRequest`
* Parent class: [`\Codefy\Framework\Http\Request\FormRequest`](./FormRequest.md)
* This class is an **Abstract class**

## Methods

### passedValidation

```php
protected passedValidation(): void
```

**Throws:**

- [`Exception`](../../../../Exception.md)

***

## Inherited methods

### validateResolved

Validate the class instance.

```php
public validateResolved(): void
```

**Throws:**

- [`UnauthorizedException`](../../Auth/Rbac/Exception/UnauthorizedException.md)
- [`Exception`](../../../../Exception.md)

***

### prepareForValidation

Prepare the data for validation.

```php
protected prepareForValidation(): void
```

***

### getValidatorInstance

Get the validator instance for the request.

```php
protected getValidatorInstance(): \Qubus\Validation\Validation
```

**Throws:**

- [`Exception`](../../../../Exception.md)

***

### passedValidation

Handle a passed validation attempt.

```php
protected passedValidation(): void
```

***

### passesAuthorization

Determine if the request passes the authorization check.

```php
protected passesAuthorization(): bool
```

***

### failedValidation

Handle a failed validation attempt.

```php
protected failedValidation(?string $message = null, int $code = 422): void
```

**Parameters:**

| Parameter  | Type        | Description |
|------------|-------------|-------------|
| `$message` | **?string** |             |
| `$code`    | **int**     |             |

**Throws:**

- [`ValidationException`](../../../../Qubus/Validation/ValidationException.md)
- [`JsonException`](../../../../JsonException.md)

***

### failedAuthorization

```php
protected failedAuthorization(): void
```

**Throws:**

- [`UnauthorizedException`](../../Auth/Rbac/Exception/UnauthorizedException.md)

***

### all

Return all input data as an array.

```php
public all(): array
```

***

### only

Replace internal data with only the specified keys.

```php
public only(array $keys): static
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$keys`   | **array** |             |

***

### except

Replace internal data excluding the specified keys.

```php
public except(array $keys): static
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$keys`   | **array** |             |

***

### validated

Validate the request data and return validated data.

```php
public validated(): array
```

***

### value

Return validated or filtered value.

```php
public value(mixed $value, mixed $default = null): mixed
```

**Parameters:**

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `$value`   | **mixed** |             |
| `$default` | **mixed** |             |

***

### messages

Get custom messages for validator errors.

```php
protected messages(): (string|null)[]
```

***

### makeValidator

Get the validator instance for the request.

```php
protected makeValidator(): ?\Qubus\Validation\Validation
```

**Throws:**

- [`Exception`](../../../../Exception.md)

***

### createDefaultValidator

Create the default validator instance.

```php
protected createDefaultValidator(\Qubus\Validation\Factories\ValidationFactory $factory): \Qubus\Validation\Validation
```

**Parameters:**

| Parameter  | Type                                              | Description |
|------------|---------------------------------------------------|-------------|
| `$factory` | **\Qubus\Validation\Factories\ValidationFactory** |             |

**Throws:**

- [`Exception`](../../../../Exception.md)

***

### setValidator

Set the Validator instance.

```php
public setValidator(\Qubus\Validation\Validation $validator): static
```

**Parameters:**

| Parameter    | Type                             | Description |
|--------------|----------------------------------|-------------|
| `$validator` | **\Qubus\Validation\Validation** |             |

***

### setContainer

Set the container implementation.

```php
public setContainer(\Qubus\Injector\ServiceContainer $container): static
```

**Parameters:**

| Parameter    | Type                                 | Description |
|--------------|--------------------------------------|-------------|
| `$container` | **\Qubus\Injector\ServiceContainer** |             |

***

### errors

Return validation errors.

```php
public errors(): \Qubus\Validation\ErrorBag
```

***

### validationRules

Get the validation rules for this form request.

```php
protected validationRules(): (string|null)[]
```

***
