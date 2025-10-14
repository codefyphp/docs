***

# Validator





* Full name: `\Qubus\Validation\Validator`
* This class implements:
[`\Qubus\Validation\Validatable`](./Validatable.md)



## Properties


### translator

The StringTranslator implementation.

```php
public \Qubus\Validation\Translators\StringTranslator $translator
```






***

### presenceVerifier

The Presence Verifier implementation.

```php
protected ?\Qubus\Validation\Interfaces\PresenceVerifier $presenceVerifier
```






***

### failedRules

The failed validation rules.

```php
protected array $failedRules
```






***

### messages

The messages.

```php
protected ?\Qubus\Validation\MessageBag $messages
```






***

### data

The data under validation.

```php
public array $data
```






***

### files

The files under validation.

```php
protected array $files
```






***

### rules

The rules to be applied to the data.

```php
protected array $rules
```






***

### after

All the registered "after" callbacks.

```php
protected array $after
```






***

### customMessages

The array of custom error messages.

```php
public array $customMessages
```






***

### fallbackMessages

The array of fallback error messages.

```php
public array $fallbackMessages
```






***

### customAttributes

The array of custom attribute names.

```php
protected array $customAttributes
```






***

### customValues

The array of custom displayable values.

```php
public array $customValues
```






***

### extensions

All the custom validator extensions.

```php
protected array $extensions
```






***

### replacers

All the custom replacer extensions.

```php
public array $replacers
```






***

### sizeRules

The size related validation rules.

```php
protected array $sizeRules
```






***

### numericRules

The numeric related validation rules.

```php
protected array $numericRules
```






***

### implicitRules

The validation rules that imply the field is required.

```php
protected array $implicitRules
```






***

## Methods


### __construct

Create a new Validator instance.

```php
public __construct(\Qubus\Validation\Translators\StringTranslator $translator, array $data, array $rules, array $messages = [], array $customAttributes = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$translator` | **\Qubus\Validation\Translators\StringTranslator** |  |
| `$data` | **array** |  |
| `$rules` | **array** |  |
| `$messages` | **array** |  |
| `$customAttributes` | **array** |  |





***

### parseData

Parse the data and hydrate the files array.

```php
protected parseData(array $data): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |





***

### explodeRules

Explode the rules into an array of rules.

```php
protected explodeRules(array|string $rules): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$rules` | **array&#124;string** |  |





***

### after

After an after validation callback.

```php
public after(callable|string $callback): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **callable&#124;string** |  |





***

### sometimes

Add conditions to a given field based on a Closure.

```php
public sometimes(string $attribute, array|string $rules, callable $callback): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$rules` | **array&#124;string** |  |
| `$callback` | **callable** |  |





***

### each

Define a set of rules that apply to each element in an array attribute.

```php
public each(string $attribute, array|string $rules): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$rules` | **array&#124;string** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### mergeRules

Merge additional rules into a given attribute.

```php
public mergeRules(string $attribute, array|string $rules): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$rules` | **array&#124;string** |  |





***

### passes

Determine if the data passes the validation rules.

```php
public passes(): bool
```












***

### fails

Determine if the data fails the validation rules.

```php
public fails(): bool
```












***

### validate

Validate a given attribute against a rule.

```php
protected validate(string $attribute, string $rule): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$rule` | **string** |  |





***

### getValue

Get the value of a given attribute.

```php
protected getValue(string $attribute): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |





***

### isValidatable

Determine if the attribute is validatable.

```php
protected isValidatable(string $rule, string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$rule` | **string** |  |
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### presentOrRuleIsImplicit

Determine if the field is present, or the rule implies required.

```php
protected presentOrRuleIsImplicit(string $rule, string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$rule` | **string** |  |
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### passesOptionalCheck

Determine if the attribute passes any optional check.

```php
protected passesOptionalCheck(string $attribute): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |





***

### isImplicit

Determine if a given rule implies the attribute is required.

```php
protected isImplicit(string $rule): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$rule` | **string** |  |





***

### addFailure

Add a failed rule and error message to the collection.

```php
protected addFailure(string $attribute, string $rule, array $parameters): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### addError

Add an error message to the validator's collection of messages.

```php
protected addError(string $attribute, string $rule, array $parameters): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### validateSometimes

"Validate" optional attributes.

```php
protected validateSometimes(): bool
```

Always returns true, just lets us put sometimes in rules.










***

### validateRequired

Validate that a required attribute exists.

```php
protected validateRequired(string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateFilled

Validate the given attribute is filled if it is present.

```php
protected validateFilled(string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### anyFailingRequired

Determine if any of the given attributes fail the required test.

```php
protected anyFailingRequired(array $attributes): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attributes` | **array** |  |





***

### allFailingRequired

Determine if all the given attributes fail the required test.

```php
protected allFailingRequired(array $attributes): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attributes` | **array** |  |





***

### validateRequiredWith

Validate that an attribute exists when any other attribute exists.

```php
protected validateRequiredWith(string $attribute, mixed $value, mixed $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **mixed** |  |





***

### validateRequiredWithAll

Validate that an attribute exists when all other attributes exists.

```php
protected validateRequiredWithAll(string $attribute, mixed $value, mixed $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **mixed** |  |





***

### validateRequiredWithout

Validate that an attribute exists when another attribute does not.

```php
protected validateRequiredWithout(string $attribute, mixed $value, mixed $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **mixed** |  |





***

### validateRequiredWithoutAll

Validate that an attribute exists when all other attributes do not.

```php
protected validateRequiredWithoutAll(string $attribute, mixed $value, mixed $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **mixed** |  |





***

### validateRequiredIf

Validate that an attribute exists when another attribute has a given value.

```php
protected validateRequiredIf(string $attribute, mixed $value, mixed $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **mixed** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### getPresentCount

Get the number of attributes in a list that are present.

```php
protected getPresentCount(array $attributes): int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attributes` | **array** |  |





***

### validateConfirmed

Validate that an attribute has a matching confirmation.

```php
protected validateConfirmed(string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### validateSame

Validate that two attributes match.

```php
protected validateSame(string $attribute, mixed $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### validateDifferent

Validate that an attribute is different from another attribute.

```php
protected validateDifferent(string $attribute, mixed $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### validateAccepted

Validate that an attribute was "accepted".

```php
protected validateAccepted(string $attribute, mixed $value): bool
```

This validation rule implies the attribute is "required".






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateBoolean

Validate that an attribute is a boolean.

```php
protected validateBoolean(string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateArray

Validate that an attribute is an array.

```php
protected validateArray(string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateNumeric

Validate that an attribute is numeric.

```php
protected validateNumeric(string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateInteger

Validate that an attribute is an integer.

```php
protected validateInteger(string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateDigits

Validate that an attribute has a given number of digits.

```php
protected validateDigits(string $attribute, mixed $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### validateDigitsBetween

Validate that an attribute is between a given number of digits.

```php
protected validateDigitsBetween(string $attribute, mixed $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### validateSize

Validate the size of an attribute.

```php
protected validateSize(string $attribute, mixed $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### validateBetween

Validate the size of an attribute is between a set of values.

```php
protected validateBetween(string $attribute, mixed $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### validateMin

Validate the size of an attribute is greater than a minimum value.

```php
protected validateMin(string $attribute, mixed $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### validateMax

Validate the size of an attribute is less than a maximum value.

```php
protected validateMax(string $attribute, mixed $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### getSize

Get the size of an attribute.

```php
protected getSize(string $attribute, mixed $value): array|int|float|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### getStringSize

Get the size of a string.

```php
protected getStringSize(string $value): int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **string** |  |





***

### validateIn

Validate an attribute is contained within a list of values.

```php
protected validateIn(string $attribute, mixed $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |





***

### validateNotIn

Validate an attribute is not contained within a list of values.

```php
protected validateNotIn(string $attribute, mixed $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |





***

### validateUnique

Validate the uniqueness of an attribute value on a given database table.

```php
protected validateUnique(string $attribute, mixed $value, array $parameters): bool
```

If a database column is not specified, the attribute will be used.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### getUniqueIds

Get the excluded ID column and value for the unique rule.

```php
protected getUniqueIds(array $parameters): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$parameters` | **array** |  |





***

### getUniqueExtra

Get the extra conditions for a unique rule.

```php
protected getUniqueExtra(array $parameters): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$parameters` | **array** |  |





***

### validateExists

Validate the existence of an attribute value in a database table.

```php
protected validateExists(string $attribute, mixed $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### getExistCount

Get the number of records that exist in storage.

```php
protected getExistCount(string $table, string $column, mixed $value, array $parameters): int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$table` | **string** |  |
| `$column` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |





***

### getExtraExistConditions

Get the extra exist conditions.

```php
protected getExtraExistConditions(array $parameters): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$parameters` | **array** |  |





***

### getExtraConditions

Get the extra conditions for a unique / exists rule.

```php
protected getExtraConditions(array $segments): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$segments` | **array** |  |





***

### validateIp

Validate that an attribute is a valid IP.

```php
protected validateIp(string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateIpv4

Validate that an attribute is a valid IPv4.

```php
protected validateIpv4(string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateIpv6

Validate that an attribute is a valid IPv6.

```php
protected validateIpv6(string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateEmail

Validate that an attribute is a valid e-mail address.

```php
protected validateEmail(string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateUrl

Validate that an attribute is a valid URL.

```php
protected validateUrl(string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateActiveUrl

Validate that an attribute is an active URL.

```php
protected validateActiveUrl(string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateImage

Validate the MIME type of file is an image MIME type.

```php
protected validateImage(string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateMimes

Validate the MIME type of file upload attribute is in a set of MIME types.

```php
protected validateMimes(string $attribute, array $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **array** |  |
| `$parameters` | **array** |  |





***

### validateAlpha

Validate that an attribute contains only alphabetic characters.

```php
protected validateAlpha(string $attribute, mixed $value): bool|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateAlphaNum

Validate that an attribute contains only alphanumeric characters.

```php
protected validateAlphaNum(string $attribute, mixed $value): bool|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateAlphaDash

Validate that an attribute contains only alphanumeric characters, dashes, and underscores.

```php
protected validateAlphaDash(string $attribute, mixed $value): bool|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateRegex

Validate that an attribute passes a regular expression check.

```php
protected validateRegex(string $attribute, mixed $value, array $parameters): bool|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### validateDate

Validate that an attribute is a valid date.

```php
protected validateDate(string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### validateDateFormat

Validate that an attribute matches a date format.

```php
protected validateDateFormat(string $attribute, mixed $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### validateBefore

Validate the date is before a given date.

```php
protected validateBefore(string $attribute, mixed $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### validateBeforeWithFormat

Validate the date is before a given date with a given format.

```php
protected validateBeforeWithFormat(string $format, mixed $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$format` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |





***

### validateAfter

Validate the date is after a given date.

```php
protected validateAfter(string $attribute, mixed $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### validateAfterWithFormat

Validate the date is after a given date with a given format.

```php
protected validateAfterWithFormat(string $format, mixed $value, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$format` | **string** |  |
| `$value` | **mixed** |  |
| `$parameters` | **array** |  |





***

### checkDateTimeOrder

Given two date/time strings, check that one is after the other.

```php
protected checkDateTimeOrder(string $format, string $before, string $after): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$format` | **string** |  |
| `$before` | **string** |  |
| `$after` | **string** |  |





***

### getDateTimeWithOptionalFormat

Get a DateTime instance from a string.

```php
protected getDateTimeWithOptionalFormat(string $format, string $value): \DateTime|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$format` | **string** |  |
| `$value` | **string** |  |





***

### validateTimezone

Validate that an attribute is a valid timezone.

```php
protected validateTimezone(string $attribute, mixed $value): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |




**Throws:**

- [`Exception`](../../Exception.md)



***

### getDateFormat

Get the date format for an attribute if it has one.

```php
protected getDateFormat(string $attribute): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |





***

### getMessage

Get the validation message for an attribute and rule.

```php
protected getMessage(string $attribute, string $rule): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$rule` | **string** |  |





***

### getInlineMessage

Get the inline message for a rule if it exists.

```php
protected getInlineMessage(string $attribute, string $lowerRule, array|null $source = null): mixed|void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$lowerRule` | **string** |  |
| `$source` | **array&#124;null** |  |





***

### getSizeMessage

Get the proper error message for an attribute and size rule.

```php
protected getSizeMessage(string $attribute, string $rule): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$rule` | **string** |  |





***

### getAttributeType

Get the data type of the given attribute.

```php
protected getAttributeType(string $attribute): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |





***

### doReplacements

Replace all error message place-holders with actual values.

```php
protected doReplacements(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### getAttributeList

Transform an array of attributes to their displayable form.

```php
protected getAttributeList(array $values): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$values` | **array** |  |





***

### getAttribute

Get the displayable name of the attribute.

```php
protected getAttribute(string $attribute): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |





***

### getDisplayableValue

Get the displayable name of the value.

```php
public getDisplayableValue(string $attribute, mixed $value): mixed|string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$value` | **mixed** |  |





***

### replaceBetween

Replace all place-holders for the between rule.

```php
protected replaceBetween(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceDigits

Replace all place-holders for the digits rule.

```php
protected replaceDigits(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceDigitsBetween

Replace all place-holders for the digits (between) rule.

```php
protected replaceDigitsBetween(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceSize

Replace all place-holders for the size rule.

```php
protected replaceSize(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceMin

Replace all place-holders for the min rule.

```php
protected replaceMin(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceMax

Replace all place-holders for the max rule.

```php
protected replaceMax(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceIn

Replace all place-holders for the in rule.

```php
protected replaceIn(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceNotIn

Replace all place-holders for the not_in rule.

```php
protected replaceNotIn(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceMimes

Replace all place-holders for the mimes rule.

```php
protected replaceMimes(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceRequiredWith

Replace all place-holders for the required_with rule.

```php
protected replaceRequiredWith(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceRequiredWithAll

Replace all place-holders for the required_with_all rule.

```php
protected replaceRequiredWithAll(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceRequiredWithout

Replace all place-holders for the required_without rule.

```php
protected replaceRequiredWithout(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceRequiredWithoutAll

Replace all place-holders for the required_without_all rule.

```php
protected replaceRequiredWithoutAll(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceRequiredIf

Replace all place-holders for the required_if rule.

```php
protected replaceRequiredIf(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceSame

Replace all place-holders for the same rule.

```php
protected replaceSame(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceDifferent

Replace all place-holders for the different rule.

```php
protected replaceDifferent(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceDateFormat

Replace all place-holders for the date_format rule.

```php
protected replaceDateFormat(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceBefore

Replace all place-holders for the before rule.

```php
protected replaceBefore(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### replaceAfter

Replace all place-holders for the after rule.

```php
protected replaceAfter(string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### hasRule

Determine if the given attribute has a rule in the given set.

```php
protected hasRule(string $attribute, array|string $rules): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$rules` | **array&#124;string** |  |





***

### getRule

Get a rule and its parameters for a given attribute.

```php
protected getRule(string $attribute, array|string $rules): array|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attribute` | **string** |  |
| `$rules` | **array&#124;string** |  |





***

### parseRule

Extract the rule name and parameters from a rule.

```php
protected parseRule(array|string $rules): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$rules` | **array&#124;string** |  |





***

### parseArrayRule

Parse an array based rule.

```php
protected parseArrayRule(array $rules): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$rules` | **array** |  |





***

### parseStringRule

Parse a string based rule.

```php
protected parseStringRule(string $rules): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$rules` | **string** |  |





***

### parseParameters

Parse a parameter list.

```php
protected parseParameters(string $rule, string $parameter): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$rule` | **string** |  |
| `$parameter` | **string** |  |





***

### addExtensions

Register an array of custom validator extensions.

```php
public addExtensions(array $extensions): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$extensions` | **array** |  |





***

### addImplicitExtensions

Register an array of custom implicit validator extensions.

```php
public addImplicitExtensions(array $extensions): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$extensions` | **array** |  |





***

### addExtension

Register a custom validator extension.

```php
public addExtension(string $rule, string|\Closure $extension): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$rule` | **string** |  |
| `$extension` | **string&#124;\Closure** |  |





***

### addImplicitExtension

Register a custom implicit validator extension.

```php
public addImplicitExtension(string $rule, string|\Closure $extension): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$rule` | **string** |  |
| `$extension` | **string&#124;\Closure** |  |





***

### addReplacers

Register an array of custom validator message replacers.

```php
public addReplacers(array $replacers): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$replacers` | **array** |  |





***

### addReplacer

Register a custom validator message replacer.

```php
public addReplacer(string $rule, string|\Closure $replacer): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$rule` | **string** |  |
| `$replacer` | **string&#124;\Closure** |  |





***

### getRules

Get the validation rules.

```php
public getRules(): array
```












***

### setRules

Set the validation rules.

```php
public setRules(array $rules): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$rules` | **array** |  |





***

### setAttributeNames

Set the custom attributes on the validator.

```php
public setAttributeNames(array $attributes): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attributes` | **array** |  |





***

### setValueNames

Set the custom values on the validator.

```php
public setValueNames(array $values): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$values` | **array** |  |





***

### getFiles

Get the files under validation.

```php
public getFiles(): array
```












***

### setFiles

Set the files under validation.

```php
public setFiles(array $files): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$files` | **array** |  |





***

### getPresenceVerifier

Get the Presence Verifier implementation.

```php
public getPresenceVerifier(): \Qubus\Validation\Interfaces\PresenceVerifier|null
```












***

### setPresenceVerifier

Set the Presence Verifier implementation.

```php
public setPresenceVerifier(\Qubus\Validation\Interfaces\PresenceVerifier $presenceVerifier): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$presenceVerifier` | **\Qubus\Validation\Interfaces\PresenceVerifier** |  |





***

### addCustomAttributes

Add custom attributes to the validator.

```php
public addCustomAttributes(array $customAttributes): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$customAttributes` | **array** |  |





***

### addCustomValues

Add the custom values for the validator.

```php
public addCustomValues(array $customValues): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$customValues` | **array** |  |





***

### failed

Get the failed validation rules.

```php
public failed(): array
```












***

### messages

Get the message container for the validator.

```php
public messages(): \Qubus\Validation\MessageBag
```












***

### errors

An alternative more semantic shortcut to the message container.

```php
public errors(): \Qubus\Validation\MessageBag
```












***

### callExtension

Call a custom validator extension.

```php
protected callExtension(string $rule, array $parameters): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### callClassBasedExtension

Call a class based validator extension.

```php
protected callClassBasedExtension(string $callback, array $parameters): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **string** |  |
| `$parameters` | **array** |  |





***

### callReplacer

Call a custom validator message replacer.

```php
protected callReplacer(string $message, string $attribute, string $rule, array $parameters): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### callClassBasedReplacer

Call a class based validator message replacer.

```php
protected callClassBasedReplacer(string $callback, string $message, string $attribute, string $rule, array $parameters): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **string** |  |
| `$message` | **string** |  |
| `$attribute` | **string** |  |
| `$rule` | **string** |  |
| `$parameters` | **array** |  |





***

### requireParameterCount

Require a certain number of parameters to be present.

```php
protected requireParameterCount(int $count, array $parameters, string $rule): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$count` | **int** |  |
| `$parameters` | **array** |  |
| `$rule` | **string** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### __call

Handle dynamic calls to class methods.

```php
public __call(string $method, array $parameters): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$method` | **string** |  |
| `$parameters` | **array** |  |




**Throws:**

- [`BadMethodCallException`](../../BadMethodCallException.md)



***


***
> Automatically generated on 2025-10-13
