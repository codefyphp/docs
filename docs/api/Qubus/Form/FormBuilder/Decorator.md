# Decorator

Decorator base class

***

* Full name: `\Qubus\Form\FormBuilder\Decorator`
* This class is an **Abstract class**

## Properties

### deep

Whether to indent each individual child node.

```php
protected bool $deep
```

***

## Methods

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
