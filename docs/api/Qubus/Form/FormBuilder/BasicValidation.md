# BasicValidation

Basic input validation
 - Server side equivalent of HTML5 validation.

- Process upload errors.
- Client side support for minlength and matching element values (using JavaScript).

***

* Full name: `\Qubus\Form\FormBuilder\BasicValidation`

## Methods

### validateRequired

Validate if the control has a value if it's required.

```php
protected validateRequired(): bool
```

***
### validateMinMax

Validate if min and max for value.

```php
protected validateMinMax(): bool
```

***
### validateLength

Validate the length of the value.

```php
protected validateLength(): bool
```

***
### validatePattern

Validate the value of the control against a regex pattern.

```php
protected validatePattern(): bool
```

***
### validateMatch

Match value against another control.

```php
protected validateMatch(): bool
```

***
### validateUpload

Check if there were upload errors.

```php
protected validateUpload(): bool
```

***
### validateType

Validate if value matches the input type.

```php
protected validateType(): bool
```

***
### validateTypeColor

Validate the value for 'color' input type.

```php
protected validateTypeColor(): bool
```

***
### validateTypeNumber

Validate the value for 'number' input type.

```php
protected validateTypeNumber(): bool
```

***
### validateTypeRange

Validate the value for 'range' input type.

```php
protected validateTypeRange(): bool
```

***
### validateTypeDate

Validate the value for 'date' input type.

```php
protected validateTypeDate(): bool
```

***
### validateTypeDatetime

Validate the value for 'datetime' input type.

```php
protected validateTypeDatetime(): bool
```

***
### validateTypeDatetimeLocal

Validate the value for 'datetime' input type.

```php
protected validateTypeDatetimeLocal(): bool
```

***
### validateTypeTime

Validate the value for 'datetime' input type.

```php
protected validateTypeTime(): bool
```

***
### validateTypeMonth

Validate the value for 'month' input type.

```php
protected validateTypeMonth(): bool
```

***
### validateTypeWeek

Validate the value for 'week' input type.

```php
protected validateTypeWeek(): bool
```

***
### validateTypeUrl

Validate the value for 'url' input type.

```php
protected validateTypeUrl(): bool
```

***
### validateTypeEmail

Validate the value for 'email' input type.

```php
protected validateTypeEmail(): bool
```

***
### getValidationScript

Get JavaScript for custom validation.

```php
public getValidationScript(): string
```

***
### getValidationScriptRules

Get the rules to build up the validation script

```php
protected getValidationScriptRules(): array
```

***
### generateValidationScript

Generate validation script

```php
protected generateValidationScript(array $rules): string
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$rules`  | **array** |             |

***
### getValidationScriptMinlength

Get script to match the minimum length

```php
protected getValidationScriptMinlength(): string|null
```

***
### getValidationScriptMatch

Get script to match other element

```php
protected getValidationScriptMatch(): string|null
```

***
### parseForScript

Parse a message, inserting values for placeholders for JavaScript.

```php
public parseForScript(string $message): string
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$message` | **string** |             |

***
### resolvePlaceholderForScript

Get a value for a placeholder for JavaScript.

```php
protected resolvePlaceholderForScript(string $var): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$var`    | **string** |             |

***
