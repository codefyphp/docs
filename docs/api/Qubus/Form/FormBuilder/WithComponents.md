# WithComponents

Element that exists of several components.

***

* Full name: `\Qubus\Form\FormBuilder\WithComponents`

## Methods

### newComponent

Initialise component

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

**Return Value:**

$this

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

***

### renderElement

Render to base HTML element.

```php
public renderElement(): string
```

***
