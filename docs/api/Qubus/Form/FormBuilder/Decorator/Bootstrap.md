# Bootstrap

Decorator base class

***

* Full name: `\Qubus\Form\FormBuilder\Decorator\Bootstrap`
* Parent class: [`\Qubus\Form\FormBuilder\Decorator`](../Decorator.md)

## Properties

### defaultFontset

Prefix for the default fontawesome fontset.

```php
public static string $defaultFontset
```

* This property is **static**.

***

## Methods

### __construct

Class constructor

```php
public __construct(array $options = []): mixed
```

**Parameters:**

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `$options` | **array** |             |

**Throws:**

- [`Exception`](../../../../Exception.md)

***

### isDeep

Whether to apply the decorator to all descendants.

```php
public isDeep(): bool
```

***

### apply

Apply modifications

```php
public apply(\Qubus\Form\FormBuilder\Element $element, bool $deep): void
```

**Parameters:**

| Parameter  | Type                                | Description |
|------------|-------------------------------------|-------------|
| `$element` | **\Qubus\Form\FormBuilder\Element** |             |
| `$deep`    | **bool**                            |             |

**Throws:**

- [`TypeException`](../../../Exception/Data/TypeException.md)
- [`Exception`](../../../Exception/Exception.md)

***

### applyToElement

Apply modifications to element

```php
protected applyToElement(\Qubus\Form\FormBuilder\Element $element): void
```

**Parameters:**

| Parameter  | Type                                | Description |
|------------|-------------------------------------|-------------|
| `$element` | **\Qubus\Form\FormBuilder\Element** |             |

**Throws:**

- [`TypeException`](../../../Exception/Data/TypeException.md)
- [`Exception`](../../../Exception/Exception.md)

***

### applyToAddon

Render prepend or append HTML.

```php
protected applyToAddon(string $placement, \Qubus\Form\FormBuilder\Element|\Qubus\Form\FormBuilder\WithComponents $element): void
```

**Parameters:**

| Parameter    | Type                                                                        | Description |
|--------------|-----------------------------------------------------------------------------|-------------|
| `$placement` | **string**                                                                  |             |
| `$element`   | **\Qubus\Form\FormBuilder\Element\|\Qubus\Form\FormBuilder\WithComponents** |             |

**Throws:**

- [`TypeException`](../../../Exception/Data/TypeException.md)
- [`Exception`](../../../Exception/Exception.md)

***

### applyToLabel

Apply modifications to label

```php
public applyToLabel(\Qubus\Form\FormBuilder\Element|\Qubus\Form\FormBuilder\WithComponents $element): void
```

**Parameters:**

| Parameter  | Type                                                                        | Description |
|------------|-----------------------------------------------------------------------------|-------------|
| `$element` | **\Qubus\Form\FormBuilder\Element\|\Qubus\Form\FormBuilder\WithComponents** |             |

***

### applyToContainer

Apply modifications to container

```php
public applyToContainer(\Qubus\Form\FormBuilder\Element|\Qubus\Form\FormBuilder\WithComponents $element): void
```

**Parameters:**

| Parameter  | Type                                                                        | Description |
|------------|-----------------------------------------------------------------------------|-------------|
| `$element` | **\Qubus\Form\FormBuilder\Element\|\Qubus\Form\FormBuilder\WithComponents** |             |

***

### renderContent

Render the content of the element control to HTML.

```php
public renderContent(\Qubus\Form\FormBuilder\Element|\Qubus\Form\FormBuilder\WithComponents $element, string $html): string
```

**Parameters:**

| Parameter  | Type                                                                        | Description            |
|------------|-----------------------------------------------------------------------------|------------------------|
| `$element` | **\Qubus\Form\FormBuilder\Element\|\Qubus\Form\FormBuilder\WithComponents** |                        |
| `$html`    | **string**                                                                  | Original rendered html |

***

### render

Render the element control to HTML.

```php
public render(\Qubus\Form\FormBuilder\Element|\Qubus\Form\FormBuilder\WithComponents $element, string $html): string
```

**Parameters:**

| Parameter  | Type                                                                        | Description            |
|------------|-----------------------------------------------------------------------------|------------------------|
| `$element` | **\Qubus\Form\FormBuilder\Element\|\Qubus\Form\FormBuilder\WithComponents** |                        |
| `$html`    | **string**                                                                  | Original rendered html |

**Throws:**

- [`Exception`](../../../Exception/Exception.md)

***

### renderControl

Render form control

```php
protected renderControl(\Qubus\Form\FormBuilder\Element|\Qubus\Form\FormBuilder\WithComponents $element, \Qubus\Form\FormBuilder\Group $container): void
```

**Parameters:**

| Parameter    | Type                                                                        | Description |
|--------------|-----------------------------------------------------------------------------|-------------|
| `$element`   | **\Qubus\Form\FormBuilder\Element\|\Qubus\Form\FormBuilder\WithComponents** |             |
| `$container` | **\Qubus\Form\FormBuilder\Group**                                           |             |

**Throws:**

- [`Exception`](../../../Exception/Exception.md)

***

### isButton

Check if element is a button

```php
protected static isButton(\Qubus\Form\FormBuilder\Element $element): bool
```

* This method is **static**.
**Parameters:**

| Parameter  | Type                                | Description |
|------------|-------------------------------------|-------------|
| `$element` | **\Qubus\Form\FormBuilder\Element** |             |

***

### register

Register Boostrap decorator and elements

```php
public static register(): void
```

* This method is **static**.
***

### icon

HTML for font icons (like FontAwesome)

```php
public static icon(string $icon, string|null $fontset = null): string
```

* This method is **static**.
**Parameters:**

| Parameter  | Type             | Description                   |
|------------|------------------|-------------------------------|
| `$icon`    | **string**       | Icon name (and other options) |
| `$fontset` | **string\|null** | Prefix for fonts              |

***

## Inherited methods

### isDeep

Whether to apply the decorator to all descendants.

```php
public isDeep(): bool
```

***

### apply

Apply modifications.

```php
public apply(\Qubus\Form\FormBuilder\Element $element, bool $deep): mixed
```

**Parameters:**

| Parameter  | Type                                | Description                                      |
|------------|-------------------------------------|--------------------------------------------------|
| `$element` | **\Qubus\Form\FormBuilder\Element** |                                                  |
| `$deep`    | **bool**                            | The decorator of a parent is applied to a child. |

***

### validate

Validate the element

```php
public validate(\Qubus\Form\FormBuilder\Element $element, bool $valid): bool
```

**Parameters:**

| Parameter  | Type                                | Description                       |
|------------|-------------------------------------|-----------------------------------|
| `$element` | **\Qubus\Form\FormBuilder\Element** |                                   |
| `$valid`   | **bool**                            | Result of FormBuilder validation. |

***

### filter

Modify the value.

```php
public filter(\Qubus\Form\FormBuilder\Element $element, mixed $value): mixed
```

**Parameters:**

| Parameter  | Type                                | Description |
|------------|-------------------------------------|-------------|
| `$element` | **\Qubus\Form\FormBuilder\Element** |             |
| `$value`   | **mixed**                           |             |

***

### render

Render to HTML

```php
public render(\Qubus\Form\FormBuilder\Element $element, string $html): string
```

**Parameters:**

| Parameter  | Type                                | Description             |
|------------|-------------------------------------|-------------------------|
| `$element` | **\Qubus\Form\FormBuilder\Element** |                         |
| `$html`    | **string**                          | Original rendered html. |

***

### renderContent

Render the element content to HTML

```php
public renderContent(\Qubus\Form\FormBuilder\Element $element, string $html): string
```

**Parameters:**

| Parameter  | Type                                | Description             |
|------------|-------------------------------------|-------------------------|
| `$element` | **\Qubus\Form\FormBuilder\Element** |                         |
| `$html`    | **string**                          | Original rendered html. |

***

### applyToValidationScript

```php
public applyToValidationScript(\Qubus\Form\FormBuilder\Control $param, array $rules): mixed
```

**Parameters:**

| Parameter | Type                                | Description |
|-----------|-------------------------------------|-------------|
| `$param`  | **\Qubus\Form\FormBuilder\Control** |             |
| `$rules`  | **array**                           |             |

***
