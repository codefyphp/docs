# FormRequestErrorResponder

***

* Full name: `\Codefy\Framework\Http\Middleware\Request\FormRequestErrorResponder`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Properties

### responseFactory

```php
private \Psr\Http\Message\ResponseFactoryInterface $responseFactory
```

***

### streamFactory

```php
private \Psr\Http\Message\StreamFactoryInterface $streamFactory
```

***

## Methods

### __construct

```php
public __construct(\Psr\Http\Message\ResponseFactoryInterface $responseFactory, \Psr\Http\Message\StreamFactoryInterface $streamFactory): mixed
```

**Parameters:**

| Parameter          | Type                                           | Description |
|--------------------|------------------------------------------------|-------------|
| `$responseFactory` | **\Psr\Http\Message\ResponseFactoryInterface** |             |
| `$streamFactory`   | **\Psr\Http\Message\StreamFactoryInterface**   |             |

***

### unauthorized

```php
public unauthorized(): \Psr\Http\Message\ResponseInterface
```

***

### validationFailed

```php
public validationFailed(array $errors): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$errors` | **array** |             |

***
