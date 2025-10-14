***

# Factory





* Full name: `\Qubus\Validation\Factory`



## Properties


### translator

The StringTranslator implementation.

```php
protected \Qubus\Validation\Translators\StringTranslator $translator
```






***

### verifier

The Presence Verifier implementation.

```php
protected ?\Qubus\Validation\Interfaces\PresenceVerifier $verifier
```






***

### extensions

All the custom validator extensions.

```php
protected array $extensions
```






***

### implicitExtensions

All the custom implicit validator extensions.

```php
protected array $implicitExtensions
```






***

### replacers

All the custom validator message replacers.

```php
protected array $replacers
```






***

### fallbackMessages

All the fallback messages for custom rules.

```php
protected array $fallbackMessages
```






***

### resolver

The Validator resolver instance.

```php
protected ?\Closure $resolver
```






***

## Methods


### __construct

Create a new Validator factory instance.

```php
public __construct(?\Qubus\Validation\Translators\StringTranslator $translator = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$translator` | **?\Qubus\Validation\Translators\StringTranslator** |  |





***

### make

Create a new Validator instance.

```php
public make(array $data, array $rules, array $messages = [], array $customAttributes = []): \Qubus\Validation\Validator
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |
| `$rules` | **array** |  |
| `$messages` | **array** |  |
| `$customAttributes` | **array** |  |





***

### addExtensions

Add the extensions to a validator instance.

```php
protected addExtensions(\Qubus\Validation\Validator $validator): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$validator` | **\Qubus\Validation\Validator** |  |





***

### resolve

Resolve a new Validator instance.

```php
protected resolve(array $data, array $rules, array $messages, array $customAttributes): \Qubus\Validation\Validator
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |
| `$rules` | **array** |  |
| `$messages` | **array** |  |
| `$customAttributes` | **array** |  |





***

### extend

Register a custom validator extension.

```php
public extend(string $rule, string|\Closure $extension, string|null $message = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$rule` | **string** |  |
| `$extension` | **string&#124;\Closure** |  |
| `$message` | **string&#124;null** |  |





***

### extendImplicit

Register a custom implicit validator extension.

```php
public extendImplicit(string $rule, string|\Closure $extension, string|null $message = null): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$rule` | **string** |  |
| `$extension` | **string&#124;\Closure** |  |
| `$message` | **string&#124;null** |  |





***

### replacer

Register a custom implicit validator message replacer.

```php
public replacer(string $rule, string|\Closure $replacer): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$rule` | **string** |  |
| `$replacer` | **string&#124;\Closure** |  |





***

### resolver

Set the Validator instance resolver.

```php
public resolver(\Closure $resolver): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$resolver` | **\Closure** |  |





***

### getTranslator

Get the StringTranslator implementation.

```php
public getTranslator(): \Qubus\Validation\Translators\StringTranslator
```












***

### getPresenceVerifier

Get the Presence Verifier implementation.

```php
public getPresenceVerifier(): \Qubus\Validation\Interfaces\PresenceVerifier
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


***
> Automatically generated on 2025-10-13
