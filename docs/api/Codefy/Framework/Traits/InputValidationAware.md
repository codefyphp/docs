# InputValidationAware

***

* Full name: `\Codefy\Framework\Traits\InputValidationAware`

## Methods

### validateResolved

Validate the class instance.

```php
public validateResolved(): void
```

**Throws:**

- [`UnauthorizedException`](../Auth/Rbac/Exception/UnauthorizedException.md)
- [`Exception`](../../../Exception.md)

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

- [`Exception`](../../../Exception.md)

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

- [`ValidationException`](../../../Qubus/Validation/ValidationException.md)
- [`JsonException`](../../../JsonException.md)

***
### failedAuthorization

```php
protected failedAuthorization(): void
```

**Throws:**

- [`UnauthorizedException`](../Auth/Rbac/Exception/UnauthorizedException.md)

***
