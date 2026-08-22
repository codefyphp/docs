---
title: Validation
sidebar_title: Validation
summary: Validate PHP input with pipe or array rules, nested fields, wildcards, aliases, defaults, custom messages, translations, and reusable rule objects.
keywords: php-validation,input-validation,validation-rules
order: 99
---

Qubus Validation is a framework-agnostic PHP library for validating arrays. It supports pipe-style and programmatic rules, nested data, wildcards, custom messages, file uploads, callbacks, and application-defined rules. Codefy Framework builds on the same library with request-aware data validators and DTO integration.

## Installation

```shell
composer require qubus/validation
```

## Quick start

```php
<?php

declare(strict_types=1);

use Qubus\Validation\Validator;

$validator = new Validator();

$validation = $validator->validate(
    inputs: [
        'name' => 'Ada Lovelace',
        'email' => 'ada@example.com',
        'password' => 'correct horse battery staple',
        'password_confirmation' => 'correct horse battery staple',
    ],
    rules: [
        'name' => 'required|string|min:2|max:100',
        'email' => 'required|email',
        'password' => 'required|string|min:12',
        'password_confirmation' => 'required|same:password',
    ],
);

if ($validation->fails()) {
    print_r($validation->errors()->firstOfAll());
}

$data = $validation->getValidData();
```

`Validator::validate()` creates and immediately runs a validation. It returns the completed `Validation` instance, not a boolean.

Use `make()` when aliases, messages, or other per-validation settings must be configured before validation runs:

```php
$validation = $validator->make($input, $rules);
$validation->setAlias('password_confirmation', 'password confirmation');
$validation->setMessages([
    'password_confirmation:same' => 'The two passwords must match.',
]);
$validation->validate();
```

!!! note
    `make()` and `validate()` accept the same input, rules, and optional messages. The difference is that `make()` leaves execution to the caller.

## Defining rules

### Pipe syntax

Separate rules with `|`. Parameters follow `:` and are normally comma-separated.

```php
$rules = [
    'username' => 'required|alpha_dash|min:3|max:30',
    'role' => 'required|in:admin,editor,viewer',
];
```

### Array syntax and rule objects

An attribute may use an array containing rule names, configured `Rule` instances, or closures:

```php
$minimumAge = $validator('min', 18);
$minimumAge->message('You must be at least 18.');

$rules = [
    'age' => ['required', 'integer', $minimumAge],
    'invite_code' => [
        'required',
        static fn (mixed $value): bool => $value === 'QUBUS',
    ],
];
```

Calling the validator as a function clones a registered rule and fills its parameters:

```php
$emailRule = $validator('email');
$rangeRule = $validator('between', 18, 120);
```

This form preserves parameter types. Pipe parameters are always strings, so use rule objects for typed defaults and parameters containing the pipe delimiter:

```php
$defaultRule = $validator('default', false);
$regexRule = $validator('regex', '/^(draft|published)$/');

$rules = [
    'enabled' => [$defaultRule, 'boolean'],
    'status' => ['required', $regexRule],
];
```

Commas are preserved inside a pipe-style `regex` parameter. A regex containing `|` must use a rule object because `|` separates validation rules.

## Empty, optional, nullable, and default values

The library considers these values empty:

- `null`
- A string that is empty after trimming
- An empty array

The values `0`, `'0'`, and `false` are not empty.

Attributes are optional unless an implicit rule such as `required`, `present`, or a conditional `required_*` rule applies. Ordinary rules are skipped for an optional empty value:

```php
$rules = [
    'display_name' => 'string|min:2',
    'email' => 'required|email',
    'middle_name' => 'nullable|string|min:2',
];
```

- Missing or empty `display_name` is allowed.
- Missing or empty `email` fails.
- Empty `middle_name` skips every rule because it is `nullable`.

`nullable` skips all rules for an empty value, including `required` and `present`. Do not combine them expecting the implicit rule to run. Use `present` by itself when a key must exist but may contain an empty value.

The `default`/`defaults` rule replaces an empty value before later rules execute:

```php
$rules = [
    'status' => 'default:draft|in:draft,published',
    'enabled' => [$validator('default', false), 'boolean'],
];
```

## Nested data and wildcards

Use dot notation for nested arrays and `*` for every item in a collection:

```php
$input = [
    'user' => ['email' => 'ada@example.com'],
    'items' => [
        ['sku' => 'ABC-1', 'quantity' => 2],
        ['sku' => 'XYZ-9', 'quantity' => 1],
    ],
];

$rules = [
    'user.email' => 'required|email',
    'items' => 'required|array',
    'items.*.sku' => 'required|alpha_dash',
    'items.*.quantity' => 'required|integer|min:1',
];
```

Comparison and conditional rules resolve wildcard siblings in the same row:

```php
$rules = [
    'users.*.password' => 'required|string|min:12',
    'users.*.password_confirmation' => 'required|same:users.*.password',
    'users.*.company' => 'required_if:users.*.account_type,business',
];
```

Wildcard messages can include zero-based `[0]` or one-based `{0}` indexes. Deeper wildcard levels use `[1]`, `{1}`, and so on:

```php
$validation = $validator->validate($input, $rules, [
    'items.*.sku:required' => 'Item {0} needs a SKU.',
]);
```

## Attribute aliases and humanized names

Attribute names are humanized by default. For example, `password_confirmation` becomes `Password confirmation` in an error message.

Configure explicit aliases before calling `validate()`:

```php
$validation = $validator->make($input, $rules);
$validation->setAlias('zip_code', 'Postal code');
$validation->setAliases([
    'state_id' => 'State',
    'items.*.sku' => 'item {0} SKU',
]);
$validation->validate();
```

An alias may also follow an input key after `:`. Rules continue to use the unaliased key:

```php
$input = ['zip_code:Postal code' => '90210'];
$rules = ['zip_code' => 'required|digits:5'];
```

Aliases may contain additional colons. Disable automatic humanization for exact input keys:

```php
$validator->setUseHumanizedKeys(false);
```

Read the current setting with `$validator->isUsingHumanizedKey()`. Use `$validation->getAlias('zip_code')` to inspect an explicitly configured alias.

## Custom messages and translations

### Validator-wide messages

Messages passed to the constructor or `setMessages()` apply to every validation created by that validator:

```php
$validator = new Validator([
    'required' => ':attribute debe llenarse.',
]);

$validator->setMessages([
    'email' => ':attribute no es una dirección válida.',
]);
```

### Per-validation messages

Pass messages as the third argument or configure the `Validation` instance before running it:

```php
$validation = $validator->validate(
    inputs: $input,
    rules: $rules,
    messages: [
        'email:email' => ':value is not a valid email address.',
    ],
);
```

```php
$validation = $validator->make($input, $rules);
$validation->setMessages([
    'age:min' => 'You must be at least :min.',
]);
$validation->validate();
```

### Message lookup order

The most specific matching message wins:

1. Explicit attribute and rule, such as `items.0.sku:required`
2. Wildcard attribute and rule, such as `items.*.sku:required`
3. Explicit attribute, such as `email`
4. Wildcard attribute, such as `items.*.sku`
5. Rule name, such as `required`
6. The rule's built-in message

### Message placeholders

- `:attribute` — alias or humanized attribute name
- `:value` — current value; arrays and objects are JSON encoded
- Rule parameters such as `:min`, `:max`, `:format`, and `:allowed_values`
- Wildcard indexes such as `[0]` and `{0}`

Translations customize joining words used by list-based messages:

```php
$validator->setTranslation('or', 'ou');
$validator->setTranslations([
    'or' => 'ou',
    'and' => 'et',
]);
```

## Validation results

```php
if ($validation->passes()) {
    $valid = $validation->getValidData();
}

if ($validation->fails()) {
    $invalid = $validation->getInvalidData();
}

$evaluated = $validation->getValidatedData();
```

- `getValidData()` returns values whose rule sets passed.
- `getInvalidData()` returns values with one or more failures.
- `getValidatedData()` combines both sets.
- Nested and wildcard paths are rebuilt as nested arrays.

### Error bag

`errors()` returns a `Countable` `ErrorBag`:

```php
$errors = $validation->errors();

count($errors);
$errors->has('email');
$errors->has('email:required');
$errors->has('items.*.sku');
$errors->first('email');
$errors->first('email:email');
$errors->get('email');
$errors->all();
$errors->firstOfAll();
$errors->firstOfAll(dotNotation: true);
$errors->toArray();
```

Methods that accept a format replace `:message`:

```php
$errors->all('<li>:message</li>');
$errors->get('email', '[error] :message');
```

`firstOfAll()` returns nested keys by default. Pass `dotNotation: true` to keep keys such as `user.email` flat.

## Complete rule reference

Ordinary rules allow an absent or empty optional value. Add `required` when a value must be supplied.

### Presence and conditional rules

#### `required`

The value must not be `null`, a blank string, or an empty array. For an attribute that also uses `uploaded_file`, a file must have been selected.

```php
'name' => 'required'
```

#### `present`

The input key must exist, but its value may be empty. Rules after `present` still run for an empty value.

```php
'nickname' => 'present'
```

#### `nullable`

If the value is empty, skip every rule on the attribute.

```php
'published_at' => 'nullable|date:Y-m-d'
```

#### `default` / `defaults`

Replace an empty value with the supplied default before subsequent rules run. Both names invoke the same rule.

```php
'status' => 'default:draft|in:draft,published'
'enabled' => [$validator('defaults', false), 'boolean']
```

#### `required_if`

Require the value when another field loosely equals any listed value.

```php
'company_name' => 'required_if:account_type,business,enterprise'
```

#### `required_unless`

Require the value unless another field loosely equals one of the listed values.

```php
'tax_id' => 'required_unless:country,US,CA'
```

#### `required_with`

Require the value when any referenced key exists. Existence, rather than whether the referenced value is empty, activates the rule.

```php
'phone_extension' => 'required_with:phone,mobile'
```

#### `required_with_all`

Require the value when every referenced key exists.

```php
'address_line_2' => 'required_with_all:address_line_1,city'
```

#### `required_without`

Require the value when any referenced key is absent.

```php
'contact_email' => 'required_without:phone,mobile'
```

#### `required_without_all`

Require the value when every referenced key is absent.

```php
'contact_email' => 'required_without_all:phone,mobile'
```

### Type rules

#### `string`

The value must be a PHP string.

```php
'title' => 'required|string'
```

#### `array`

The value must be a PHP array.

```php
'tags' => 'required|array'
```

#### `numeric`

The value must satisfy PHP's `is_numeric()` check. Numeric strings are accepted.

```php
'price' => 'required|numeric|min:0'
```

#### `integer` / `int`

The value must be accepted by `FILTER_VALIDATE_INT`. PHP integers and canonical integer strings are accepted. Both names invoke the same rule.

```php
'quantity' => 'required|integer|min:1'
'position' => 'required|int|min:0'
```

#### `boolean` / `bool`

The value must be one of `true`, `false`, `'true'`, `'false'`, `1`, `0`, `'1'`, `'0'`, `'y'`, or `'n'`. Both names invoke the same rule.

```php
'remember_me' => 'required|boolean'
'enabled' => 'required|bool'
```

This rule validates accepted representations; it does not coerce them to a PHP boolean.

#### `json`

The value must be a non-empty string containing valid JSON.

```php
'metadata' => 'required|json'
```

#### `enum`

The value must be a PHP `UnitEnum` case or an enum class name.

```php
enum UserRole
{
    case Admin;
    case Editor;
}

$input = ['role' => UserRole::Admin];
$rules = ['role' => 'required|enum'];
```

An enum class string also passes:

```php
$input = ['enum_type' => UserRole::class];
$rules = ['enum_type' => 'required|enum'];
```

The rule does not convert or validate a backing scalar such as `'admin'` against a specified enum class. Convert backing values with `UserRole::from()` or `UserRole::tryFrom()` first.

### String-content rules

The alphabetic rules are Unicode-aware.

#### `alpha`

Only Unicode letters and combining marks are allowed.

```php
'first_name' => 'required|alpha'
```

#### `alpha_num`

Only Unicode letters, combining marks, and numbers are allowed.

```php
'account_code' => 'required|alpha_num'
```

#### `alpha_dash`

Unicode letters, combining marks, numbers, underscores, and hyphens are allowed.

```php
'slug' => 'required|alpha_dash'
```

#### `alpha_spaces`

Unicode letters, combining marks, and whitespace are allowed.

```php
'full_name' => 'required|alpha_spaces'
```

#### `lowercase`

The value must be a string already in lowercase. Unicode case conversion is supported.

```php
'username' => 'required|string|lowercase'
```

#### `uppercase`

The value must be a string already in uppercase. Unicode case conversion is supported.

```php
'country_code' => 'required|string|uppercase'
```

#### `regex`

The value must match a valid PHP regular expression.

```php
'hex_color' => 'required|regex:/^#[0-9a-f]{6}$/i'
```

Use a rule object for a pattern containing `|`:

```php
'status' => ['required', $validator('regex', '/^(draft|published)$/')]
```

A malformed regular expression fails validation. Omitting the pattern is a configuration error and throws `MissingRequiredParameterException`.

#### `digits`

The value must contain exactly the requested number of ASCII digits. Integers and digit strings are accepted.

```php
'pin' => 'required|digits:4'
```

#### `digits_between`

The value must contain an inclusive range of ASCII digits.

```php
'account_number' => 'required|digits_between:8,12'
```

### Format rules

#### `email`

The value must be a valid email address according to `FILTER_VALIDATE_EMAIL`.

```php
'email' => 'required|email'
```

#### `url`

The value must be a valid URL. With no parameter, the library requires a `scheme://` form. Restrict accepted schemes by listing them; matching is case-insensitive.

```php
'website' => 'required|url:http,https'
'support_email' => 'required|url:mailto'
'database_dsn' => 'required|url:jdbc'
```

The `mailto` variant accepts `mailto:user@example.com`. The `jdbc` variant accepts forms such as `jdbc:mysql://localhost/database`.

#### `ip`

The value must be a valid IPv4 or IPv6 address.

```php
'client_ip' => 'required|ip'
```

#### `ipv4`

The value must be a valid IPv4 address.

```php
'gateway' => 'required|ipv4'
```

#### `ipv6`

The value must be a valid IPv6 address.

```php
'gateway' => 'required|ipv6'
```

#### `uuid`

The value must be a valid, non-nil UUID.

```php
'request_id' => 'required|uuid'
```

#### `ulid`

The value must be a 26-character ULID using the Crockford Base32 alphabet. Uppercase and lowercase input are accepted.

```php
'event_id' => 'required|ulid'
```

#### `date`

The value must exactly match the specified `DateTimeImmutable` format. The default is `Y-m-d`. Invalid calendar dates, parse warnings, and trailing data fail.

```php
'birthday' => 'required|date'
'appointment' => 'required|date:d/m/Y'
```

#### `before`

The value must be strictly before the supplied date/time. Both expressions are parsed with `strtotime()`.

```php
'starts_at' => 'required|before:2030-01-01'
```

Invalid date expressions throw an exception instead of producing an ordinary validation failure.

#### `after`

The value must be strictly after the supplied date/time. Both expressions are parsed with `strtotime()`.

```php
'expires_at' => 'required|after:today'
```

Invalid date expressions throw an exception instead of producing an ordinary validation failure.

### Value and comparison rules

#### `accepted`

The value must strictly equal one of `yes`, `on`, `'1'`, `1`, `true`, or `'true'`.

```php
'terms' => 'required|accepted'
```

#### `in`

The value must loosely equal one of the allowed values.

```php
'role' => 'required|in:admin,editor,viewer'
```

Use a rule object for typed choices and optional strict comparison:

```php
$inRule = $validator('in', ['1', '2']);
$inRule->strict();

$rules = ['level' => ['required', $inRule]];
```

#### `not_in`

The value must not loosely equal any disallowed value.

```php
'username' => 'required|not_in:admin,root,system'
```

Strict comparison is also available:

```php
$notInRule = $validator('not_in', [0, false]);
$notInRule->strict();

$rules = ['value' => ['required', $notInRule]];
```

#### `same`

The value must loosely equal another attribute.

```php
'password_confirmation' => 'required|same:password'
```

#### `different`

The value must be strictly different from another attribute.

```php
'new_email' => 'required|different:current_email'
```

Both comparison rules support dot notation and wildcard sibling resolution.

#### `min`

The value's size must be at least the supplied size.

```php
'age' => 'required|integer|min:18'
'username' => 'required|string|min:3'
'tags' => 'required|array|min:1'
```

#### `max`

The value's size must not exceed the supplied size.

```php
'price' => 'required|numeric|max:999.99'
'title' => 'required|string|max:120'
'tags' => 'array|max:10'
```

#### `between`

The value's size must be inside the inclusive range.

```php
'rating' => 'required|numeric|between:1,5'
'summary' => 'required|string|between:20,500'
```

For `min`, `max`, and `between`:

- Integers and floats use their numeric value.
- Numeric strings use their numeric value when the attribute also has `numeric`, `integer`, or `int`.
- Other strings use their multibyte character length.
- Arrays use their element count.
- Uploaded file arrays use their size in bytes.

File sizes may use `B`, `K`/`KB`, `M`/`MB`, `G`/`GB`, `T`/`TB`, or `P`/`PB`, including decimal values such as `1.5MB`.

### File rules

File rules operate on native PHP upload arrays containing `name`, `type`, `tmp_name`, `error`, and `size`.

#### `extension`

The path or filename must end with one of the listed extensions. Matching is case-insensitive and leading dots in the allowed list are ignored. This rule checks only the name; it does not inspect file content.

```php
'report_name' => 'required|extension:pdf,csv'
```

#### `uploaded_file`

The value must be a successful PHP upload and may be constrained by minimum size, maximum size, and MIME-derived extension. The parameter order is `minimum,maximum,type...`:

```php
$input = $_POST + $_FILES;

$rules = [
    'avatar' => 'required|uploaded_file:0,500K,png,jpeg',
    'document' => 'required|uploaded_file:,10MB,pdf',
];
```

Leave a position empty when that boundary is not needed. The programmatic API is useful for dynamic constraints:

```php
$upload = $validator('uploaded_file');
$upload->sizeBetween('10K', '2MB');
$upload->fileTypes(['png', 'jpeg']);

$rules = ['avatar' => ['required', $upload]];
```

The rule verifies the native upload shape, `is_uploaded_file()`, the upload error, size limits, and allowed type. Nested structures produced by `$_FILES` are normalized when `uploaded_file` is used with dot notation or wildcards.

#### `mimes`

The successful PHP upload's reported MIME type must map to one of the listed extension labels.

```php
'avatar' => 'required|mimes:png,jpeg'
```

The client-provided MIME type is not a security boundary. Applications should independently inspect untrusted file content, generate safe filenames, and move uploads to a controlled location.

### MIME type lookup utility

`MimeTypeGuesser` exposes the mapping used by the upload rules:

```php
use Qubus\Validation\MimeTypeGuesser;

$guesser = new MimeTypeGuesser();

$extension = $guesser->getExtension('image/jpeg'); // 'jpeg'
$mimeType = $guesser->getMimeType('jpeg');         // 'image/jpeg'
```

Both methods return `null` when the mapping is unknown. Extension aliases are mapping-specific; normalize application input to a supported label.

### Callback rule

#### `callback`

A closure in a rule array is converted to a callback rule automatically. Return `false` for the default error, return a string for a custom error, and return any other value to pass:

```php
$rules = [
    'even_number' => [
        'required',
        'integer',
        static function (mixed $value): bool|string {
            return ((int) $value % 2 === 0)
                ? true
                : 'The :attribute must be even.';
        },
    ],
];
```

Create the rule explicitly when it must be reused:

```php
$notBlocked = $validator(
    'callback',
    static fn (mixed $value): bool => $value !== 'blocked',
);

$rules = ['status' => ['required', $notBlocked]];
```

A non-static closure is bound to the callback rule and can access methods such as `$this->getAttribute()`. Static closures are not rebound.

## Custom rules

Create a `Rule` subclass and implement `check()`:

```php
<?php

declare(strict_types=1);

namespace App\Validation;

use Qubus\Validation\Rule;

final class Even extends Rule
{
    protected string $message = 'The :attribute must be even.';

    public function check(mixed $value): bool
    {
        return is_int($value) && $value % 2 === 0;
    }
}
```

Register the rule before using it:

```php
$validator->addValidator('even', new App\Validation\Even());

$validation = $validator->validate(
    ['number' => 4],
    ['number' => 'required|even'],
);
```

Built-in rule names cannot be replaced by default. Intentional overrides must be enabled first:

```php
$validator->allowRuleOverride(true);
$validator->addValidator('required', new App\Validation\CustomRequired());
```

Rules can expose programmatic configuration through their own methods. The built-in `uploaded_file`, `url`, `in`, and `not_in` rules use this pattern.

### Parameterized custom rules

Declare fillable parameter names when a rule accepts pipe parameters. Those parameter names are also available as message placeholders:

```php
<?php

declare(strict_types=1);

namespace App\Validation;

use Qubus\Validation\Rule;

final class DivisibleBy extends Rule
{
    protected array $fillableParams = ['divisor'];

    protected string $message = 'The :attribute must be divisible by :divisor.';

    public function check(mixed $value): bool
    {
        $this->requireParameters($this->fillableParams);

        $divisor = (int) $this->parameter('divisor');

        return is_int($value)
            && $divisor !== 0
            && $value % $divisor === 0;
    }
}
```

```php
$validator->addValidator('divisible_by', new App\Validation\DivisibleBy());

$rules = [
    'quantity' => 'required|integer|divisible_by:3',
];
```

Rule authors can use:

- `parameter()`, `setParameter()`, `setParameters()`, and `getParameters()` for configuration
- `setParameterText()` when the error-facing text should differ from the raw value
- `message()`/`setMessage()` and `getMessage()` for error text
- `getAttribute()` to inspect the current `Attribute`
- `$this->validation` in a subclass to inspect sibling input or translations
- `protected bool $implicit = true` when a rule must run for missing or empty input

### Rule lifecycle interfaces

Implement `Qubus\Validation\Rules\Interfaces\BeforeValidate` when a rule must normalize or prepare data before any attribute is checked. Its `beforeValidate(): void` method is called during the pre-validation pass. The built-in `uploaded_file` rule uses this hook to normalize nested `$_FILES` structures.

Implement `Qubus\Validation\Rules\Interfaces\ModifyValue` when a rule replaces the value seen by later rules. Its `modifyValue(mixed $value): mixed` result becomes the current value and is included in validation result data. The built-in `default`/`defaults` rule uses this mechanism.

### Registered-rule API

`addValidator()` is the safe registration API because it protects built-in names. Advanced integrations can inspect or replace the registry directly:

```php
$required = $validator->getValidator('required');

$validator->setValidator('application_rule', new App\Validation\ApplicationRule());
```

`setValidator()` assigns the rule immediately and does not perform the override check used by `addValidator()`. Prefer `addValidator()` for application extensions. Use `allowRuleOverride(true)` only when replacing a built-in is deliberate.

The validator and validation message/translation traits also expose singular and bulk accessors:

```php
$validator->setMessage('required', ':attribute is mandatory.');
$validator->setMessages($messages);
$validator->getMessage('required');
$validator->getMessages();

$validator->setTranslation('or', 'ou');
$validator->setTranslations($translations);
$validator->getTranslation('or');
$validator->getTranslations();
```

### Dynamic attributes and input

A `Validation` may be extended or inspected before it runs:

```php
$validation = $validator->make($input, $rules);
$validation->addAttribute('profile.timezone', 'required|string');

$attribute = $validation->getAttribute('profile.timezone');
$hasEmail = $validation->hasValue('email');
$email = $validation->getValue('email');
$validation->setValue('email', strtolower((string) $email));

$validation->validate();
```

`getValidator()` on a `Validation` returns its parent `Validator`, which is useful to construct another configured rule in advanced integrations. Prefer preparing all attributes and values before validation; mutations made afterward are not evaluated until `validate()` is called again.

## Reusing a validation

Calling `validate()` again clears the previous errors and result data, overlays the supplied top-level input values, and evaluates every rule again:

```php
$validation = $validator->make(
    ['email' => 'invalid'],
    ['email' => 'required|email'],
);

$validation->validate();
assert($validation->fails());

$validation->validate(['email' => 'valid@example.com']);
assert($validation->passes());
```

New top-level values replace previous values with the same key. Values not supplied to the later call remain available.

## Validation factory

Applications using dependency injection can depend on `ValidationFactory`:

```php
use Qubus\Validation\Factories\ValidationFactory;

$validation = ValidationFactory::make(
    inputs: $input,
    rules: $rules,
    messages: $messages,
);

$validation->validate();
```

Like `Validator::make()`, the factory returns an unexecuted `Validation` instance.

## PSR-7 and framework integration

The core package validates arrays and does not depend on a request implementation. Extract request data before validation:

```php
$input = array_merge(
    $request->getQueryParams(),
    (array) $request->getParsedBody(),
);

$validation = $validator->validate($input, $rules);
```

Core upload rules expect native PHP upload arrays. If a request implementation returns PSR-7 `UploadedFileInterface` objects, adapt them to the documented upload shape or use the framework's upload abstraction.

## Exceptions

Rule failures are collected in `ErrorBag`; they are not thrown. Invalid configuration can throw:

- `Qubus\Validation\RuleNotFoundException` when a rule is not registered
- `Qubus\Validation\MissingRequiredParameterException` when a rule parameter is absent
- `Qubus\Validation\RuleOverrideException` when a registered name is replaced without enabling overrides
- `Qubus\Exception\Data\TypeException` when a callback or configured value has the wrong type
- `Exception` for invalid `before`/`after` date expressions and certain construction errors

## Codefy Framework data validators

Codefy Framework's `HttpInputValidator` adapts this package to a PSR-7 request. It provides:

- A request-specific validator class with reusable rules and messages
- Optional authorization before validation
- Query, parsed-body, and uploaded-file input aggregation
- `only()` and `except()` filtering
- Typed value accessors
- Validation lifecycle hooks
- Optional DTO conversion with `UseDto` and `DtoAware`

### Define a request validator

Create one class for each application action. Keeping the action verb in the name—such as `StoreUserValidator` or `UpdateUserValidator`—makes the intended rules clear.

```php
<?php

declare(strict_types=1);

namespace Domain\User\Validator;

use Codefy\Framework\Validation\HttpInputValidator;
use Domain\User\Enum\UserRole;

use function Codefy\Framework\Helpers\gate;

final class StoreUserValidator extends HttpInputValidator
{
    public function authorize(): bool
    {
        return (bool) gate('admin:create:user');
    }

    /**
     * @return array<string, string>
     */
    public function rules(): array
    {
        $roles = implode(
            ',',
            array_map(
                static fn (UserRole $role): string => $role->value,
                UserRole::cases(),
            ),
        );

        return [
            'username' => 'required|alpha_dash|min:3|max:30',
            'first_name' => 'required|string|min:2|max:100',
            'middle_name' => 'nullable|string|min:2|max:100',
            'last_name' => 'required|string|min:2|max:100',
            'email' => 'required|email',
            'role' => 'required|string|in:' . $roles,
            'password' => 'required|string|min:12',
        ];
    }

    /**
     * @return array<string, string>
     */
    protected function messages(): array
    {
        return [
            'username:alpha_dash' => 'Username may contain letters, numbers, dashes, and underscores.',
            'role:in' => 'Choose a supported user role.',
        ];
    }
}
```

`authorize()` is optional. Without it, authorization passes. A false result causes Codefy to throw `UnauthorizedException` with status code 401 before any validation runs.

`messages()` is also optional and uses the same keys, wildcard matching, and placeholders documented above.

### Create and execute the validator

`make()` accepts any PSR-7 `ServerRequestInterface`:

```php
$data = StoreUserValidator::make($request);
$validated = $data->validated();
```

Validation is lazy. Constructing the object does not execute it; `validated()`, `value()`, the typed accessors, and DTO conversion trigger the validation lifecycle. A failed validation throws `Qubus\Validation\ValidationException` with status code 422 and an error summary.

After all rules pass, the current Codefy implementation of `validated()` returns the validator's complete aggregated or filtered data array. It does not automatically discard keys that have no rule. Apply `only()` when the application needs an allow-list boundary.

Input is merged in this order:

1. Query parameters
2. Parsed request body
3. Uploaded files

Later sources replace an earlier value with the same top-level key.

### Filter request data

`only()` and `except()` return a cloned validator, leaving the original object unchanged:

```php
$identity = StoreUserValidator::make($request)->only([
    'username',
    'email',
]);

$withoutPassword = StoreUserValidator::make($request)->except([
    'password',
]);
```

Filtering changes the data passed into validation. Required rules for excluded keys therefore fail unless the matching rule set is also appropriate for that filtered use case.

### Read validated values

Use `value()` for a mixed value or one of the typed accessors when the runtime PHP type is known:

```php
$data = StoreUserValidator::make($request);

$username = $data->string('username');
$role = $data->string('role');
$metadata = $data->array('metadata', []);
$enabled = $data->boolean('enabled', false);
$attempts = $data->integer('attempts', 0);
$score = $data->float('score', 0.0);
```

The typed accessors verify the actual PHP type and throw `Qubus\Exception\Data\TypeException` on a mismatch. Validation rules verify values but do not coerce request strings. For example, the string `'1'` can pass `integer`, but `integer('attempts')` still requires an actual PHP `int`.

### Validation lifecycle hooks

`HttpInputValidator` uses these hooks:

1. `prepareForValidation()`
2. `authorize()` when defined
3. Rule validation
4. `failedValidation()` on failure, otherwise `passedValidation()`

Normalize data before rules execute by overriding `prepareForValidation()`:

```php
protected function prepareForValidation(): void
{
    $input = $this->all();
    $input['email'] = strtolower(trim((string) ($input['email'] ?? '')));

    $this->data = $input;
}
```

Use `passedValidation()` for local post-validation work. Avoid side effects in validation hooks when the same validator may be read more than once.

### Container and validator overrides

Codefy normally resolves `ValidationFactory` from the application container. Tests or specialized integrations may supply another container or a prebuilt core validation:

```php
$data = StoreUserValidator::make($request);
$data->setContainer($container);

$customValidation = $coreValidator->make(
    $data->all(),
    ['email' => 'required|email'],
);

$data->setValidator($customValidation);
$validated = $data->validated();
```

Both setters return the request validator for optional chaining. A prebuilt validation supplied with `setValidator()` replaces the default validation created from `rules()` and `messages()`.

### Transform validated input into a DTO

A DTO gives application and domain layers explicit types instead of passing request arrays through the system.

```php
<?php

declare(strict_types=1);

namespace Domain\User\Dto;

use Codefy\Framework\Dto\DataTransformer;
use Codefy\Framework\Support\Password;
use Codefy\Framework\Validation\DataValidator;
use Domain\User\ValueObject\Username;
use Domain\User\ValueObject\UserRole;
use Domain\User\ValueObject\UserToken;
use Qubus\ValueObjects\StringLiteral\StringLiteral;
use Qubus\ValueObjects\Web\EmailAddress;

final readonly class StoreUserData implements DataTransformer
{
    private function __construct(
        public Username $username,
        public UserToken $token,
        public StringLiteral $firstName,
        public StringLiteral $middleName,
        public StringLiteral $lastName,
        public EmailAddress $email,
        public UserRole $role,
        public StringLiteral $password,
    ) {
    }

    public static function fromValidatedData(DataValidator $data): self
    {
        return new self(
            username: new Username($data->string('username')),
            token: new UserToken(),
            firstName: new StringLiteral($data->string('first_name')),
            middleName: new StringLiteral($data->string('middle_name', '')),
            lastName: new StringLiteral($data->string('last_name')),
            email: new EmailAddress($data->string('email')),
            role: new UserRole($data->string('role')),
            password: new StringLiteral(
                Password::hash($data->string('password')),
            ),
        );
    }
}
```

The DTO implements `DataTransformer`, whose `fromValidatedData()` factory receives the Codefy `DataValidator`. Object construction and value-object conversion happen only after validation succeeds.

Use it explicitly in a controller:

```php
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

use Codefy\Framework\Http\BaseController;
use Domain\User\Command\CreateUserCommand;
use Domain\User\Dto\StoreUserData;
use Domain\User\Validator\StoreUserValidator;
use Psr\Http\Message\ResponseInterface;
use Psr\Http\Message\ServerRequestInterface;

use function Codefy\Framework\Helpers\command;

final class AdminController extends BaseController
{
    public function store(ServerRequestInterface $request): ResponseInterface
    {
        $user = StoreUserData::fromValidatedData(
            StoreUserValidator::make($request),
        );

        command(new CreateUserCommand([
            $user->username,
            $user->token,
            $user->firstName,
            $user->middleName,
            $user->lastName,
            $user->email,
            $user->role,
            $user->password,
        ]));

        return $this->redirect(
            url: $this->router->url(name: 'admin.users'),
        );
    }
}
```

### Automatic DTO conversion with `UseDto`

Implement `HasDto`, use `DtoAware`, and attach `UseDto` to associate the validator with its DTO:

```php
<?php

declare(strict_types=1);

namespace Domain\User\Validator;

use Codefy\Framework\Dto\Attribute\UseDto;
use Codefy\Framework\Dto\HasDto;
use Codefy\Framework\Dto\Trait\DtoAware;
use Codefy\Framework\Validation\HttpInputValidator;
use Domain\User\Dto\StoreUserData;

#[UseDto(StoreUserData::class)]
final class StoreUserValidator extends HttpInputValidator implements HasDto
{
    use DtoAware;

    public function authorize(): bool
    {
        return true;
    }

    /**
     * @return array<string, string>
     */
    public function rules(): array
    {
        return [
            'username' => 'required|alpha_dash|min:3|max:30',
            'first_name' => 'required|string|min:2|max:100',
            'middle_name' => 'nullable|string|min:2|max:100',
            'last_name' => 'required|string|min:2|max:100',
            'email' => 'required|email',
            'role' => 'required|string|in:admin,editor',
            'password' => 'required|string|min:12',
        ];
    }
}
```

`DtoAware` provides:

- `getDtoClass()` to read the class from `UseDto`
- `toDto()` to validate and call the DTO's `fromValidatedData()` factory
- `toDtoArray()` to return the DTO's public properties as an array
- Runtime errors when the DTO class or factory method is missing

```php
$validator = StoreUserValidator::make($request);

/** @var StoreUserData $user */
$user = $validator->toDto();
$commandData = $validator->toDtoArray();
```

`toDtoArray()` uses `get_object_vars()` and therefore contains only public DTO properties. Nested value objects remain objects; this method does not recursively serialize them.

### Pass a validator into a service

Passing the validator lets the service choose a DTO or array boundary while the controller remains small:

```php
<?php

declare(strict_types=1);

namespace Domain\User\Service;

use Domain\User\Command\CreateUserCommand;
use Domain\User\Validator\StoreUserValidator;

use function Codefy\Framework\Helpers\command;

final readonly class UserService
{
    public function createUser(StoreUserValidator $data): void
    {
        command(new CreateUserCommand(
            data: $data->toDtoArray(),
        ));
    }
}
```

```php
public function store(
    ServerRequestInterface $request,
    UserService $service,
): ResponseInterface {
    $service->createUser(StoreUserValidator::make($request));

    return $this->redirect(
        url: $this->router->url(name: 'admin.users'),
    );
}
```

Choose one application boundary consistently: pass a DTO when services should be independent of HTTP validation, or pass the validator when the service intentionally owns DTO conversion.

### Uploaded Files

`HttpInputValidator::all()` includes values returned by the PSR-7 request's `getUploadedFiles()`. Those are normally `UploadedFileInterface` objects, while the core `uploaded_file` and `mimes` rules consume native PHP upload arrays. Use the request/framework upload facilities or normalize files before applying the core upload rules.
