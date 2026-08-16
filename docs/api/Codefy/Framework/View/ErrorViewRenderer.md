# ErrorViewRenderer

***

* Full name: `\Codefy\Framework\View\ErrorViewRenderer`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Properties

### app

```php
private \Codefy\Framework\Application $app
```

***

### fileSystem

```php
private \Qubus\FileSystem\FileSystem $fileSystem
```

***

## Methods

### __construct

```php
public __construct(\Codefy\Framework\Application $app, \Qubus\FileSystem\FileSystem $fileSystem): mixed
```

**Parameters:**

| Parameter     | Type                              | Description |
|---------------|-----------------------------------|-------------|
| `$app`        | **\Codefy\Framework\Application** |             |
| `$fileSystem` | **\Qubus\FileSystem\FileSystem**  |             |

***

### render

```php
public render(int $code): string
```

**Parameters:**

| Parameter | Type    | Description |
|-----------|---------|-------------|
| `$code`   | **int** |             |

**Throws:**

- [`NotFoundException`](../../../Qubus/Exception/Http/Client/NotFoundException.md)
- [`Exception`](../../../Exception.md)

***

### toResponse

```php
public toResponse(string $html): \Psr\Http\Message\ResponseInterface
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$html`   | **string** |             |

**Throws:**

- [`Exception`](../../../Exception.md)

***

### loadTemplate

```php
private loadTemplate(): string
```

**Throws:**

- [`NotFoundException`](../../../Qubus/Exception/Http/Client/NotFoundException.md)
- [`Exception`](../../../Exception.md)

***

### replaceTags

```php
private replaceTags(string $template, int $code, string $message): string
```

**Parameters:**

| Parameter   | Type       | Description |
|-------------|------------|-------------|
| `$template` | **string** |             |
| `$code`     | **int**    |             |
| `$message`  | **string** |             |

***
