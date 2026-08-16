# Validator

***

* Full name: `\Qubus\Validation\Validator`

## Properties

### translations

```php
protected array $translations
```

***

### validators

```php
protected array $validators
```

***

### allowRuleOverride

```php
protected bool $allowRuleOverride
```

***

### useHumanizedKeys

```php
protected bool $useHumanizedKeys
```

***

## Methods

### __construct

```php
public __construct(array $messages = []): void
```

**Parameters:**

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `$messages` | **array** |             |

***

### setValidator

Register or override existing validator.

```php
public setValidator(mixed $key, \Qubus\Validation\Rule $rule): void
```

**Parameters:**

| Parameter | Type                       | Description |
|-----------|----------------------------|-------------|
| `$key`    | **mixed**                  |             |
| `$rule`   | **\Qubus\Validation\Rule** |             |

***

### getValidator

Get validator object from given $key.

```php
public getValidator(mixed $key): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$key`    | **mixed** |             |

***

### validate

Validate $inputs.

```php
public validate(array $inputs, array $rules, array $messages = []): \Qubus\Validation\Validation
```

**Parameters:**

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `$inputs`   | **array** |             |
| `$rules`    | **array** |             |
| `$messages` | **array** |             |

**Throws:**

- [`MissingRequiredParameterException`](./MissingRequiredParameterException.md)
- [`TypeException`](../Exception/Data/TypeException.md)
- [`Exception`](../../Exception.md)

***

### make

Given $inputs, $rules and $messages to make the Validation class instance.

```php
public make(array $inputs, array $rules, array $messages = []): \Qubus\Validation\Validation
```

**Parameters:**

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `$inputs`   | **array** |             |
| `$rules`    | **array** |             |
| `$messages` | **array** |             |

**Throws:**

- [`Exception`](../../Exception.md)

***

### __invoke

Magic invoke method to make Rule instance.

```php
public __invoke(string $rule): \Qubus\Validation\Rule
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$rule`   | **string** |             |

**Throws:**

- [`RuleNotFoundException`](./RuleNotFoundException.md)

***

### registerBaseValidators

Initialize base validators array.

```php
protected registerBaseValidators(): void
```

***

### addValidator

Given $ruleName and $rule to add new validator.

```php
public addValidator(string $ruleName, \Qubus\Validation\Rule $rule): void
```

**Parameters:**

| Parameter   | Type                       | Description |
|-------------|----------------------------|-------------|
| `$ruleName` | **string**                 |             |
| `$rule`     | **\Qubus\Validation\Rule** |             |

**Throws:**

- [`RuleOverrideException`](./RuleOverrideException.md)

***

### allowRuleOverride

Set rule can allow to be overridden.

```php
public allowRuleOverride(bool $status = false): void
```

**Parameters:**

| Parameter | Type     | Description |
|-----------|----------|-------------|
| `$status` | **bool** |             |

***

### setUseHumanizedKeys

Set this can use humanize keys.

```php
public setUseHumanizedKeys(bool $useHumanizedKeys = true): void
```

**Parameters:**

| Parameter           | Type     | Description |
|---------------------|----------|-------------|
| `$useHumanizedKeys` | **bool** |             |

***

### isUsingHumanizedKey

Get $this->useHumanizedKeys value.

```php
public isUsingHumanizedKey(): bool
```

***

## Inherited methods

### setMessage

Given $key and $message to set message.

```php
public setMessage(mixed $key, mixed $message): void
```

**Parameters:**

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `$key`     | **mixed** |             |
| `$message` | **mixed** |             |

***

### setMessages

Given $messages and set multiple messages.

```php
public setMessages(array $messages): void
```

**Parameters:**

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `$messages` | **array** |             |

***

### getMessage

Given message from given $key.

```php
public getMessage(string $key): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### getMessages

Get all $messages

```php
public getMessages(): array
```

***

### setTranslation

Given $key and $translation to set translation

```php
public setTranslation(mixed $key, mixed $translation): void
```

**Parameters:**

| Parameter      | Type      | Description |
|----------------|-----------|-------------|
| `$key`         | **mixed** |             |
| `$translation` | **mixed** |             |

***

### setTranslations

Given $translations and set multiple translations

```php
public setTranslations(array $translations): void
```

**Parameters:**

| Parameter       | Type      | Description |
|-----------------|-----------|-------------|
| `$translations` | **array** |             |

***

### getTranslation

Given translation from given $key

```php
public getTranslation(string $key): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### getTranslations

Get all $translations

```php
public getTranslations(): array
```

***
