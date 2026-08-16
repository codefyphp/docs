# FormBuilder

FormBuilder factory

***

* Full name: `\Qubus\Form\FormBuilder`

## Properties

### options

Default options.

```php
public static array $options
```

* This property is **static**.

***

### elements

Element types.

```php
public static array $elements
```

* This property is **static**.

***

### decorators

Decorator types.

```php
public static array $decorators
```

* This property is **static**.

***

## Methods

### element

Create a form element.

```php
public static element(string $type, array $options = [], array $attr = []): \Qubus\Form\FormBuilder\Element|\Qubus\Form\FormBuilder\Control
```

* This method is **static**.
**Parameters:**

| Parameter  | Type       | Description     |
|------------|------------|-----------------|
| `$type`    | **string** | Element type    |
| `$options` | **array**  | Element options |
| `$attr`    | **array**  | HTML attributes |

**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)

***

### decorator

Create a form decorator.

```php
public static decorator(string $type): \Qubus\Form\FormBuilder\Decorator
```

* This method is **static**.
**Parameters:**

| Parameter | Type       | Description    |
|-----------|------------|----------------|
| `$type`   | **string** | Decorator type |

**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)
- [`ReflectionException`](../../ReflectionException.md)

***
