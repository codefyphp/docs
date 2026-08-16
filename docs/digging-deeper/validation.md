---
title: Validation
sidebar_title: Validation
order: 99
---

## Installation

```shell
composer require qubus/validation
```

The validation library for validating PSR-7 Request data.

## Usage

There are two ways to validating data: 1) use the `make()` method to create a validation object, then validate it using 
the `validate()` method, 2) or just use `validate()`.

### Examples

#### Using `make()`:

```php
<?php

use Qubus\Validation\Validator;

$validator = new Validator();

// make it
$validation = $validator->make($_POST + $_FILES, [
    'name'                  => 'required',
    'email'                 => 'required|email',
    'password'              => 'required|min:6',
    'confirm_password'      => 'required|same:password',
    'avatar'                => 'required|uploaded_file:0,500K,png,jpeg',
    'skills'                => 'array',
    'skills.*.id'           => 'required|numeric',
    'skills.*.percentage'   => 'required|numeric'
]);

// then validate
$validation->validate();

if ($validation->fails()) {
    // handling errors
    $errors = $validation->errors();
    echo "<pre>";
    print_r($errors->firstOfAll());
    echo "</pre>";
    exit;
} else {
    // validation passes
    echo "Success!";
}
```

#### Using `validate()`:

```php
<?php

use Qubus\Validation\Validator;

$validator = new Validator();

$validation = $validator->validate($_POST + $_FILES, [
    'name'                  => 'required',
    'email'                 => 'required|email',
    'password'              => 'required|min:6',
    'confirm_password'      => 'required|same:password',
    'avatar'                => 'required|uploaded_file:0,500K,png,jpeg',
    'skills'                => 'array',
    'skills.*.id'           => 'required|numeric',
    'skills.*.percentage'   => 'required|numeric'
]);

if ($validation->fails()) {
	// handling errors
	$errors = $validation->errors();
	echo "<pre>";
	print_r($errors->firstOfAll());
	echo "</pre>";
	exit;
} else {
	// validation passes
	echo "Success!";
}
```

!!!note
    Both examples will output the same results. But, you may want to use the `make()` method for access to custom 
    messages, custom attribute alias, etc. before looping the validation.

### Attribute Alias

You can transform your attribute into readable text. For example `confirm_password` will be displayed as 
`Confirm password`. But you can set it to anything you want with the `setAlias()` or `setAliases()` methods.

#### Example

```php
<?php

use Qubus\Validation\Validator;

$validator = new Validator();

// To set attribute alias, you should use `make` instead of `validate`.
$validation->make([
	'state_id' => $_POST['state_id'],
	'zip_code' => $_POST['zip_code']
], [
	'state_id' => 'required|alpha',
	'zip_code' => 'required|numeric'
]);

// now you can set aliases using this way:
$validation->setAlias('state_id', 'State');
$validation->setAlias('zip_code', 'Postal Code');

// or this way:
$validation->setAliases([
	'state_id' => 'State',
	'zip_code' => 'Postal Code'
]);

// then validate it
$validation->validate();
```

Now if `state_id` value is empty, the error message will be 'State is required'.

## Custom Validation Message

Before registering or setting custom messages, you can use the following placeholders:

* `:attribute`: will replace into attribute alias.
* `:value`: will replace into a stringified value of the attribute. For arrays or objects, will replace into JSON.

Here are some ways to register/set your custom message(s):

### Custom Messages for Validator

Anytime you use `make` or `validate` you can set your custom message(s). This is useful for localization.

To accomplish this, pass an array to the constructor:

```php
<?php

use Qubus\Validation\Validator;

$validator = new Validator([
	'required' => ':attribute debe llenarse',
	'email' => ':email inválido',
	// etc
]);

// then validation will use these custom messages
$validation_a = $validator->validate(inputs: $dataset_a, rules: $rules_for_a);
$validation_b = $validator->validate(inputs: $dataset_b, rules: $rules_for_b);
```

or use the `setMessages()` method:

```php
<?php

use Qubus\Validation\Validator;

$validator = new Validator();

$validator->setMessages([
	'required' => ':attribute debe llenarse',
	'email' => ':email inválido',
	// etc
]);

// then validation will use these custom messages
$validation_a = $validator->validate(inputs: $dataset_a, rules: $rules_for_a);
$validation_b = $validator->validate(inputs: $dataset_b, rules: $rules_for_b);
```

### Custom Messages for Validation

Sometimes, you may need to set custom messages for a specific validation. To do this, you can set your custom messages 
as a 3rd argument of `$validator->make()` or `$validator->validate()`:

```php
<?php

use Qubus\Validation\Validator;

$validator = new Validator();

// then validation will use the custom messages
$validation = $validator->validate(
    inputs: $dataset_a,
    rules: $rules_for_a,
    messages: [
        'required' => ':attribute debe llenarse',
        'email' => ':email inválido',
        // etc
    ]
);
```

Or you use `$validation->setMessages()`:

```php
<?php

use Qubus\Validation\Validator;

$validator = new Validator();

$validation = $validator->make($dataset_a, $rules_for_dataset_a);
$validation->setMessages([
    'required' => ':attribute debe llenarse',
    'email' => ':email inválido',
    // etc
]);

//

$validation->validate();
```

### Custom Message for Specific Attribute Rule

Sometimes you may need to set a custom message for a specific rule attribute. To do so, you can use `:` as a message 
separator or by chaining methods.


#### Examples

```php
<?php

use Qubus\Validation\Validator;

$validator = new Validator();

$validation = $validator->make($dataset_a, [
    'age' => 'required|min:18'
]);
$validation->setMessages([
    'age:min' => '18+ only',
]);

$validation->validate();
```

or chain methods:

```php
<?php

use Qubus\Validation\Validator;

$validator = new Validator();

$validation = $validator->make($dataset_a, [
    'photo' => [
		'required',
		$validator('uploaded_file')->fileTypes('jpeg|png')->message('Photo must be a jpeg/png image')
	]
]);

$validation->validate();
```

## Data Validators

If you are using one of the starter templates for CodefyPHP, this becomes much easier with using Data Validators.

Let's create a `StoreUserValidator` with 2 methods (`authorize` and `rules`):

```php
<?php

declare(strict_types=1);

namespace Domain\User\Validator;

use Codefy\Framework\Validation\HttpInputValidator;
use Domain\User\Enum\UserRole;

use function Codefy\Framework\Helpers\gate;
use function implode;

final class StoreUserValidator extends HttpInputValidator
{
    public function authorize(): bool
    {
        return (bool) gate('admin:create:user');
    }

    /**
     * @return array<string, string>
     * @throws \Exception
     */
    public function rules(): array
    {
        $roles = implode(separator: ',', array: UserRole::values());

        return [
            'first_name' => 'required|string|min:3',
            'middle_name' => 'string|min:3',
            'last_name' => 'required|string|min:3',
            'email' => 'required|email',
            'role' => 'required|string|in:' . $roles,
        ];
    }
}
```

Now, we need a DTO to go with our validator using the same verb `Store` as a prefix. This naming convention isn't 
necessary, but it does add clarity:

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

    /**
     * @throws \Exception
     */
    public static function fromValidatedData(DataValidator $data): self
    {
        return new self(
            username: new Username($data->string(key: 'username')),
            token: new UserToken(),
            firstName: new StringLiteral($data->string(key: 'first_name')),
            middleName: new StringLiteral($data->string(key: 'middle_name', default: '')),
            lastName: new StringLiteral($data->string(key: 'last_name')),
            email: new EmailAddress($data->string(key: 'email')),
            role: new UserRole($data->string(key: 'role')),
            password: new StringLiteral(Password::hash($data->string(key: 'password'))),
        );
    }
}
```

### Usage in Controller

```php
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

use Codefy\Framework\Http\BaseController;
use Domain\User\Command\CreateUserCommand;
use Domain\User\Validator\StoreUserValidator;
use Domain\User\Service\UserService;
use Psr\Http\Message\ResponseInterface;
use Qubus\Http\ServerRequest;
use Qubus\Routing\Exceptions\NamedRouteNotFoundException;
use Qubus\Routing\Exceptions\RouteParamFailedConstraintException;

use function Codefy\Framework\Helpers\command;

final class AdminController extends BaseController
{
    /**
     * @throws RouteParamFailedConstraintException
     * @throws NamedRouteNotFoundException
     * @throws \Exception
     * @throws \ReflectionException
     */
    public function store(ServerRequest $request, UserService $service): ResponseInterface
    {
        $userData = StoreUserData::fromValidatedData(
            StoreUserValidator::make($request)
        );
        
        $command = new CreateUserCommand([
            $userData->username,
            $userData->token,
            $userData->firstName,
            $userData->middleName,
            $userData->lastName,
            $userData->email,
            $userData->role,
            $userData->password,
        ]);
        
        command(command: $command);

        return $this->redirect(
            url: $this->router->url(
                name: 'admin.users'
            )
        );
    }
}
```

### Custom DTO Class with UseDto Attribute

You can enhance your Validators by implementing the `Codefy\Framework\Dto\HasDto` interface, adding the 
`Codefy\Framework\Dto\Trait\DtoAware` trait and by using the `Codefy\Framework\Dto\Attribute\UseDto` attribute

```php
<?php

declare(strict_types=1);

namespace Domain\User\Validator;

use Codefy\Framework\Dto\Attribute\UseDto;
use Codefy\Framework\Dto\HasDto;
use Codefy\Framework\Dto\Trait\DtoAware;
use Codefy\Framework\Validation\HttpInputValidator;
use Domain\User\Dto\StoreUserData;
use Domain\User\Enum\UserRole;

use function Codefy\Framework\Helpers\gate;
use function implode;

#[UseDto(StoreUserData::class)]
final class StoreUserValidator extends HttpInputValidator implements HasDto
{
    use DtoAware;
    
    public function authorize(): bool
    {
        return (bool) gate('admin:create:user');
    }

    /**
     * @return array<string, string>
     * @throws \Exception
     */
    public function rules(): array
    {
        $roles = implode(separator: ',', array: UserRole::values());

        return [
            'first_name' => 'required|string|min:3',
            'middle_name' => 'string|min:3',
            'last_name' => 'required|string|min:3',
            'email' => 'required|email',
            'role' => 'required|string|in:' . $roles,
        ];
    }
}
```

The `Codefy\Framework\Dto\Trait\DtoAware` trait automatically:

* Resolves the correct DTO class name based on the `UseDto` attribute
* Validates that the DTO class exists
* Calls the `fromValidatedData()` method to create the DTO
* Provides helpful error messages if something goes wrong

Benefits of using the `UseDto` attribute:

✅ Custom naming conventions

✅ Reuse existing DTO classes

✅ Better organization of DTOs

✅ Type safety with class-string parameter

```php
<?php

declare(strict_types=1);

namespace Domain\User\Service;

use Codefy\CommandBus\Exceptions\CommandCouldNotBeHandledException;
use Codefy\CommandBus\Exceptions\CommandPropertyNotFoundException;
use Codefy\CommandBus\Exceptions\UnresolvableCommandHandlerException;
use Codefy\Framework\Factory\FileLoggerFactory;
use Codefy\Framework\Proxy\Codefy;
use Codefy\QueryBus\UnresolvableQueryHandlerException;
use Domain\User\Command\CreateUserCommand;
use Domain\User\Validator\StoreUserValidator;

use function Codefy\Framework\Helpers\command;
use function Codefy\Framework\Helpers\trans;

final readonly class UserService
{
    /**
     * @throws \ReflectionException
     * @throws \Exception
     */
    public function createUser(StoreUserValidator $data): void
    {
        try {
            command(
                command: new CreateUserCommand(
                    data: $data->toDtoArray()
                )
            );

            Codefy::$PHP->flash->success(
                message: trans('User added successfully.'),
            );
        } catch (CommandPropertyNotFoundException|
                \ReflectionException|
                UnresolvableCommandHandlerException|
                CommandCouldNotBeHandledException $e
        ) {
            Codefy::$PHP->flash->error(
                message: trans('Could not create user. Please try again later.'),
            );
            FileLoggerFactory::getLogger()->error(message: $e->getMessage(), context: ['AdminController' => 'create']);
        }
    }
}

```
Now when you call `$data->toDtoArray()`, it will return a data array of validated values from `StoreUserValidator`.

```php
<?php

// In your controller
public function store(ServerRequest $request, UserService $service): ResponseInterface
{
    $service->createUser(
        StoreUserValidator::make($request)
    );

    return $this->redirect(
        url: $this->router->url(
            name: 'admin.users'
        )
    );
}
```






