# FormRequest

***

* Full name: `\Codefy\Framework\Http\Middleware\Request\FormRequest`
* This class implements:
  [`\Codefy\Framework\Http\Middleware\Request\FormRequestMiddleware`](./FormRequestMiddleware.md)
* This class is an **Abstract class**

## Properties

### validator

```php
private ?\Qubus\Validation\Validation $validator
```

***

### validatorFactory

```php
protected \Qubus\Validation\Factories\ValidationFactory $validatorFactory
```

***

### errorResponder

```php
private \Codefy\Framework\Http\Middleware\Request\FormRequestErrorResponder $errorResponder
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Validation\Factories\ValidationFactory $validatorFactory, \Codefy\Framework\Http\Middleware\Request\FormRequestErrorResponder $errorResponder): mixed
```

**Parameters:**

| Parameter           | Type                                                                    | Description |
|---------------------|-------------------------------------------------------------------------|-------------|
| `$validatorFactory` | **\Qubus\Validation\Factories\ValidationFactory**                       |             |
| `$errorResponder`   | **\Codefy\Framework\Http\Middleware\Request\FormRequestErrorResponder** |             |

***

### process

```php
public process(\Psr\Http\Message\ServerRequestInterface $request, \Psr\Http\Server\RequestHandlerInterface $handler): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |
| `$handler` | **\Psr\Http\Server\RequestHandlerInterface** |             |

**Throws:**

- [`Exception`](../../../../../Exception.md)

***

### fails

```php
public fails(\Psr\Http\Message\ServerRequestInterface $request): bool
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

**Throws:**

- [`Exception`](../../../../../Exception.md)

***

### errors

```php
public errors(): array
```

***

### authorize

```php
public authorize(\Psr\Http\Message\ServerRequestInterface $request): bool
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

***

### rules

Validation rules.

```php
protected rules(): string[]
```

***

### messages

Validation messages.

```php
protected messages(): string[]
```

***

### makeValidator

```php
private makeValidator(\Psr\Http\Message\ServerRequestInterface $request): \Qubus\Validation\Validation
```

**Parameters:**

| Parameter  | Type                                         | Description |
|------------|----------------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |             |

**Throws:**

- [`Exception`](../../../../../Exception.md)

***
