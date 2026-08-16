# Validation

***

* Full name: `\Qubus\Validation\Validation`

## Properties

### validator

```php
protected mixed $validator
```

***

### inputs

```php
protected array $inputs
```

***

### attributes

```php
protected array $attributes
```

***

### aliases

```php
protected array $aliases
```

***

### messageSeparator

```php
protected string $messageSeparator
```

***

### validData

```php
protected array $validData
```

***

### invalidData

```php
protected array $invalidData
```

***

### errors

```php
public ?\Qubus\Validation\ErrorBag $errors
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Validation\Validator $validator, array $inputs, array $rules, array $messages = []): void
```

**Parameters:**

| Parameter    | Type                            | Description |
|--------------|---------------------------------|-------------|
| `$validator` | **\Qubus\Validation\Validator** |             |
| `$inputs`    | **array**                       |             |
| `$rules`     | **array**                       |             |
| `$messages`  | **array**                       |             |

**Throws:**

- [`Exception`](../../Exception.md)

***

### addAttribute

Add attribute rules.

```php
public addAttribute(string $attributeKey, array|string $rules): void
```

**Parameters:**

| Parameter       | Type              | Description |
|-----------------|-------------------|-------------|
| `$attributeKey` | **string**        |             |
| `$rules`        | **array\|string** |             |

**Throws:**

- [`Exception`](../../Exception.md)

***

### getAttribute

Get attribute by key.

```php
public getAttribute(string $attributeKey): null|\Qubus\Validation\Attribute
```

**Parameters:**

| Parameter       | Type       | Description |
|-----------------|------------|-------------|
| `$attributeKey` | **string** |             |

***

### validate

Run validation.

```php
public validate(array $inputs = []): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$inputs` | **array** |             |

**Throws:**

- [`MissingRequiredParameterException`](./MissingRequiredParameterException.md)
- [`TypeException`](../Exception/Data/TypeException.md)

***

### errors

Get ErrorBag instance.

```php
public errors(): \Qubus\Validation\ErrorBag
```

***

### validateAttribute

Validate attribute.

```php
protected validateAttribute(\Qubus\Validation\Attribute $attribute): void
```

**Parameters:**

| Parameter    | Type                            | Description |
|--------------|---------------------------------|-------------|
| `$attribute` | **\Qubus\Validation\Attribute** |             |

**Throws:**

- [`MissingRequiredParameterException`](./MissingRequiredParameterException.md)
- [`TypeException`](../Exception/Data/TypeException.md)

***

### isArrayAttribute

Check whether given $attribute is array attribute.

```php
protected isArrayAttribute(\Qubus\Validation\Attribute $attribute): bool
```

**Parameters:**

| Parameter    | Type                            | Description |
|--------------|---------------------------------|-------------|
| `$attribute` | **\Qubus\Validation\Attribute** |             |

***

### parseArrayAttribute

Parse array attribute into it's child attributes.

```php
protected parseArrayAttribute(\Qubus\Validation\Attribute $attribute): array
```

**Parameters:**

| Parameter    | Type                            | Description |
|--------------|---------------------------------|-------------|
| `$attribute` | **\Qubus\Validation\Attribute** |             |

**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)

***

### initializeAttributeOnData

Gather a copy of the attribute data filled with any missing attributes.

```php
protected initializeAttributeOnData(string $attributeKey): array
```

**Parameters:**

| Parameter       | Type       | Description |
|-----------------|------------|-------------|
| `$attributeKey` | **string** |             |

**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)

***

### extractValuesForWildcards

Get all the exact attribute values for a given wildcard attribute.

```php
public extractValuesForWildcards(array $data, string $attributeKey): array
```

**Parameters:**

| Parameter       | Type       | Description |
|-----------------|------------|-------------|
| `$data`         | **array**  |             |
| `$attributeKey` | **string** |             |

**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)

***

### getLeadingExplicitAttributePath

Get the explicit part of the attribute name.

```php
protected getLeadingExplicitAttributePath(string $attributeKey): string|null
```

E.g. 'foo.bar.*.baz' -> 'foo.bar'

Allows us to not spin through all the flattened data for some operations.

**Parameters:**

| Parameter       | Type       | Description |
|-----------------|------------|-------------|
| `$attributeKey` | **string** |             |

**Return Value:**

null when root wildcard

***

### extractDataFromPath

Extract data based on the given dot-notated path.

```php
protected extractDataFromPath(string|null $attributeKey): array
```

Used to extract a subsection of the data for faster iteration.

**Parameters:**

| Parameter       | Type             | Description |
|-----------------|------------------|-------------|
| `$attributeKey` | **string\|null** |             |

**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)

***

### addError

Add error to the $this->errors.

```php
protected addError(\Qubus\Validation\Attribute $attribute, mixed $value, \Qubus\Validation\Rule $ruleValidator): void
```

**Parameters:**

| Parameter        | Type                            | Description |
|------------------|---------------------------------|-------------|
| `$attribute`     | **\Qubus\Validation\Attribute** |             |
| `$value`         | **mixed**                       |             |
| `$ruleValidator` | **\Qubus\Validation\Rule**      |             |

***

### isEmptyValue

Check $value is empty value.

```php
protected isEmptyValue(mixed $value): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### ruleIsOptional

Check the rule is optional.

```php
protected ruleIsOptional(\Qubus\Validation\Attribute $attribute, \Qubus\Validation\Rule $rule): bool
```

**Parameters:**

| Parameter    | Type                            | Description |
|--------------|---------------------------------|-------------|
| `$attribute` | **\Qubus\Validation\Attribute** |             |
| `$rule`      | **\Qubus\Validation\Rule**      |             |

***

### resolveAttributeName

Resolve attribute name.

```php
protected resolveAttributeName(\Qubus\Validation\Attribute $attribute): string
```

**Parameters:**

| Parameter    | Type                            | Description |
|--------------|---------------------------------|-------------|
| `$attribute` | **\Qubus\Validation\Attribute** |             |

***

### resolveMessage

Resolve message.

```php
protected resolveMessage(\Qubus\Validation\Attribute $attribute, mixed $value, \Qubus\Validation\Rule $validator): mixed
```

**Parameters:**

| Parameter    | Type                            | Description |
|--------------|---------------------------------|-------------|
| `$attribute` | **\Qubus\Validation\Attribute** |             |
| `$value`     | **mixed**                       |             |
| `$validator` | **\Qubus\Validation\Rule**      |             |

***

### stringify

Stringify $value.

```php
protected stringify(mixed $value): string
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### resolveRules

Resolve $rules.

```php
protected resolveRules(mixed $rules): array
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$rules`  | **mixed** |             |

**Throws:**

- [`Exception`](../../Exception.md)

***

### parseRule

Parse $rule.

```php
protected parseRule(string $rule): array
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$rule`   | **string** |             |

***

### setAlias

Given $attributeKey and $alias then assign alias.

```php
public setAlias(mixed $attributeKey, mixed $alias): void
```

**Parameters:**

| Parameter       | Type      | Description |
|-----------------|-----------|-------------|
| `$attributeKey` | **mixed** |             |
| `$alias`        | **mixed** |             |

***

### getAlias

Get attribute alias from given key.

```php
public getAlias(mixed $attributeKey): string|null
```

**Parameters:**

| Parameter       | Type      | Description |
|-----------------|-----------|-------------|
| `$attributeKey` | **mixed** |             |

***

### setAliases

Set attributes aliases.

```php
public setAliases(array $aliases): void
```

**Parameters:**

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `$aliases` | **array** |             |

***

### passes

Check validations are passed.

```php
public passes(): bool
```

***

### fails

Check validations are failed.

```php
public fails(): bool
```

***

### getValue

Given $key and get value.

```php
public getValue(string $key): mixed
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)

***

### setValue

Set input value.

```php
public setValue(string $key, mixed $value): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |
| `$value`  | **mixed**  |             |

***

### hasValue

Given $key and check value exists.

```php
public hasValue(string $key): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### getValidator

Get Validator class instance.

```php
public getValidator(): \Qubus\Validation\Validator
```

***

### resolveInputAttributes

Given $inputs and resolve input attributes.

```php
protected resolveInputAttributes(array $inputs): array
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$inputs` | **array** |             |

***

### getValidatedData

Get validated data.

```php
public getValidatedData(): array
```

***

### setValidData

Set valid data.

```php
protected setValidData(\Qubus\Validation\Attribute $attribute, mixed $value): void
```

**Parameters:**

| Parameter    | Type                            | Description |
|--------------|---------------------------------|-------------|
| `$attribute` | **\Qubus\Validation\Attribute** |             |
| `$value`     | **mixed**                       |             |

***

### getValidData

Get valid data.

```php
public getValidData(): array
```

***

### setInvalidData

Set invalid data.

```php
protected setInvalidData(\Qubus\Validation\Attribute $attribute, mixed $value): void
```

**Parameters:**

| Parameter    | Type                            | Description |
|--------------|---------------------------------|-------------|
| `$attribute` | **\Qubus\Validation\Attribute** |             |
| `$value`     | **mixed**                       |             |

***

### getInvalidData

Get invalid data.

```php
public getInvalidData(): array
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
