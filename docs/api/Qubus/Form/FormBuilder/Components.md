# Components

Element that exists of several components.

***

* Full name: `\Qubus\Form\FormBuilder\Components`

## Properties

### components

Components

```php
protected \Qubus\Form\FormBuilder\Element[] $components
```

***

## Methods

### initComponents

Initialise default components.

```php
protected initComponents(): void
```

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)
- [`Exception`](../../Exception/Exception.md)

***
### newComponent

Create / init new component.

```php
public newComponent(string|null $name = null, string|null $type = null, array $options = [], array $attr = []): \Qubus\Form\FormBuilder\Element
```

**Parameters:**

| Parameter  | Type             | Description     |
|------------|------------------|-----------------|
| `$name`    | **string\|null** | Component name  |
| `$type`    | **string\|null** | Element type    |
| `$options` | **array**        | Element options |
| `$attr`    | **array**        | Element attr    |

**Throws:**

- [`Exception`](../../Exception/Exception.md)
- [`TypeException`](../../Exception/Data/TypeException.md)

***
### getComponent

Get a component.

```php
public getComponent(string $name): \Qubus\Form\FormBuilder\Element|null
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)
- [`Exception`](../../Exception/Exception.md)

***
### getLabel

Get label component.

```php
public getLabel(): \Qubus\Form\FormBuilder\Element
```

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)
- [`Exception`](../../Exception/Exception.md)

***
### getContainer

Get the container component.

```php
public getContainer(): \Qubus\Form\FormBuilder\Group
```

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)
- [`Exception`](../../Exception/Exception.md)

***
### render

Render the element to HTML.

```php
public render(): string
```

**Throws:**

- [`\Qubus\Exception\Data\TypeException|\Qubus\Exception\Exception`](../../Exception/Data/TypeException|/Qubus/Exception/Exception.md)

***
### renderElement

Render to base HTML element.

```php
public renderElement(): string
```

* This method is **abstract**.
***
