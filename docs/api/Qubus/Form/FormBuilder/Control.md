# Control

Base class of form control elements.

***

* Full name: `\Qubus\Form\FormBuilder\Control`
* Parent class: [`\Qubus\Form\FormBuilder\Element`](./Element.md)
* This class implements:
  [`\Qubus\Form\FormBuilder\WithComponents`](./WithComponents.md)
* This class is an **Abstract class**

## Properties

### value

Control value

```php
protected mixed $value
```

***

### error

Error message

```php
protected null|string $error
```

***

## Methods

### __construct

```php
public __construct(array $options = [], array $attr = []): mixed
```

**Parameters:**

| Parameter  | Type      | Description     |
|------------|-----------|-----------------|
| `$options` | **array** | Element options |
| `$attr`    | **array** | HTML attributes |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)
- [`Exception`](../../Exception/Exception.md)

***

### getDescription

Get the description of the element.

```php
public getDescription(): string
```

***

### setValue

Set the value of the element.

```php
public setValue(mixed $value): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$value`  | **mixed** |             |

***

### getValue

Get the value of the element.

```php
public getValue(): mixed
```

***

### setError

Set the error message.

```php
public setError(string $error): void
```

**Parameters:**

| Parameter | Type       | Description       |
|-----------|------------|-------------------|
| `$error`  | **string** | The error message |

***

### getError

Get the error message (after validation).

```php
public getError(): string|null
```

***

### resolvePlaceholder

Get a value for a placeholder.

```php
protected resolvePlaceholder(string $var): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$var`    | **string** |             |

***

## Inherited methods

### __construct

```php
public __construct(array $options = [], array $attr = []): mixed
```

**Parameters:**

| Parameter  | Type      | Description     |
|------------|-----------|-----------------|
| `$options` | **array** | Element options |
| `$attr`    | **array** | HTML attributes |

***

### addDecorator

Add a decorator to the element.

```php
public addDecorator(string|\Qubus\Form\FormBuilder\Decorator $decorator): \Qubus\Form\FormBuilder\Element
```

**Parameters:**

| Parameter    | Type                                          | Description              |
|--------------|-----------------------------------------------|--------------------------|
| `$decorator` | **string\|\Qubus\Form\FormBuilder\Decorator** | Decorator object or name |

**Return Value:**

$this

***

### applyDeepDecorators

Apply decorators from parent

```php
protected applyDeepDecorators(\Qubus\Form\FormBuilder\Group $parent): void
```

**Parameters:**

| Parameter | Type                              | Description |
|-----------|-----------------------------------|-------------|
| `$parent` | **\Qubus\Form\FormBuilder\Group** |             |

***

### getDecorators

Get all decorators

```php
public getDecorators(): \Qubus\Form\FormBuilder\Decorator[]
```

***

### convertCustomType

Convert custom (form specific) type to general factory type.

```php
protected convertCustomType(string& $type, array& $options, array& $attr = []): void
```

**Parameters:**

| Parameter  | Type       | Description              |
|------------|------------|--------------------------|
| `$type`    | **string** | (in/out) Element type    |
| `$options` | **array**  | (in/out) Element options |
| `$attr`    | **array**  | (in/out) HTML attributes |

***

### build

Factory method

```php
public build(string $type, array $options = [], array $attr = []): \Qubus\Form\FormBuilder\Element
```

**Parameters:**

| Parameter  | Type       | Description     |
|------------|------------|-----------------|
| `$type`    | **string** | Element type    |
| `$options` | **array**  | Element options |
| `$attr`    | **array**  | HTML attributes |

**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)
- [`Exception`](../../Exception/Exception.md)

***

### getForm

Get the form to which this element is added.

```php
public getForm(): \Qubus\Form\FormBuilder\Group|\Qubus\Form\FormBuilder\Element|\Qubus\Form\Form|null
```

***

### asComponentOf

Set element of which this a component of

```php
protected asComponentOf(\Qubus\Form\FormBuilder\Element $element): \Qubus\Form\FormBuilder\Element
```

**Parameters:**

| Parameter  | Type                                | Description |
|------------|-------------------------------------|-------------|
| `$element` | **\Qubus\Form\FormBuilder\Element** |             |

**Return Value:**

$this

***

### isComponent

Check if element is used as a component

```php
public isComponent(): bool
```

***

### setParent

Set parent element

```php
protected setParent(\Qubus\Form\FormBuilder\Element $parent): \Qubus\Form\FormBuilder\Element
```

**Parameters:**

| Parameter | Type                                | Description |
|-----------|-------------------------------------|-------------|
| `$parent` | **\Qubus\Form\FormBuilder\Element** |             |

**Return Value:**

$this

**Throws:**

- [`Exception`](../../Exception/Exception.md)

***

### getParent

Return parent element

```php
public getParent(): \Qubus\Form\FormBuilder\Group|null
```

***

### end

Get parent or element of which this is an component.

```php
public end(): \Qubus\Form\FormBuilder\Element|\Qubus\Form\FormBuilder\Group|null
```

***

### getId

Get element id.

```php
public getId(): string
```

***

### getName

Return the name of the control.

```php
public getName(): bool|string|null
```

***

### setAttr

Set HTML attribute(s).

```php
final public setAttr(array|string $attr, mixed|null $value = null): \Qubus\Form\FormBuilder\Element
```

* This method is **final**.
**Parameters:**

| Parameter | Type              | Description                                   |
|-----------|-------------------|-----------------------------------------------|
| `$attr`   | **array\|string** | Attribute name or assoc array with attributes |
| `$value`  | **mixed\|null**   |                                               |

**Return Value:**

$this

***

### getAttr

Get an HTML attribute(s).

```php
final public getAttr(string|null $attr = null): mixed
```

All attributes will be cased to their string representation.

* This method is **final**.
**Parameters:**

| Parameter | Type             | Description                                |
|-----------|------------------|--------------------------------------------|
| `$attr`   | **string\|null** | Attribute name, omit to get all attributes |

***

### hasClass

Check if class is present

```php
final public hasClass(string $class): bool
```

* This method is **final**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$class`  | **string** |             |

***

### addClass

Add a class

```php
final public addClass(array|string $class): \Qubus\Form\FormBuilder\Element
```

* This method is **final**.
**Parameters:**

| Parameter | Type              | Description                                                 |
|-----------|-------------------|-------------------------------------------------------------|
| `$class`  | **array\|string** | Multiple classes may be specified as array or using a space |

**Return Value:**

$this

***

### removeClass

Remove a class

```php
public removeClass(array|string $class): \Qubus\Form\FormBuilder\Element
```

**Parameters:**

| Parameter | Type              | Description                                                 |
|-----------|-------------------|-------------------------------------------------------------|
| `$class`  | **array\|string** | Multiple classes may be specified as array or using a space |

**Return Value:**

$this

***

### setOption

Set an option or array with options

```php
public setOption(array|string $option, mixed|null $value = null): \Qubus\Form\FormBuilder\Element
```

**Parameters:**

| Parameter | Type              | Description                       |
|-----------|-------------------|-----------------------------------|
| `$option` | **array\|string** | Option name or array with options |
| `$value`  | **mixed\|null**   |                                   |

**Return Value:**

$this

***

### getOption

Get an option.

```php
public getOption(string $option): mixed
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$option` | **string** |             |

***

### getOptions

Get all options.

```php
public getOptions(): array
```

Bubbles to combine options of parent/ancestors.

***

### isValid

Validate the element.

```php
final public isValid(): bool
```

* This method is **final**.
***

### validate

Standard validation for the element

```php
protected validate(): bool
```

***

### setContent

Set element content

```php
public setContent(\Closure|string $content): $this
```

**Parameters:**

| Parameter  | Type                 | Description     |
|------------|----------------------|-----------------|
| `$content` | **\Closure\|string** | Content as HTML |

***

### getContent

Get the element content

```php
final public getContent(): string|null
```

* This method is **final**.
***

### renderContent

Render the element content

```php
protected renderContent(): string|null
```

***

### render

Render the element to HTML.

```php
public render(): string
```

**Throws:**

- [`\Qubus\Exception\Data\TypeException|\Qubus\Exception\Exception`](../../Exception/Data/TypeException|/Qubus/Exception/Exception.md)

***

### toHTML

Render the element to HTML.

```php
final public toHTML(): string
```

* This method is **final**.
***

### __toString

Render the element to HTML.

```php
final public __toString(): string
```

* This method is **final**.
***

### parse

Parse a message, inserting values for placeholders.

```php
public parse(string $message): string
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$message` | **string** |             |

***

### resolvePlaceholder

Get a value for a placeholder

```php
protected resolvePlaceholder(string|array $var): string
```

**Parameters:**

| Parameter | Type              | Description |
|-----------|-------------------|-------------|
| `$var`    | **string\|array** |             |

***

### convertTo

Convert an element to another type.

```php
public convertTo(string $type): \Qubus\Form\FormBuilder\Element
```

Simply returns $this if element is already of correct type.

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$type`   | **string** |             |

***

### __clone

Magic method called after cloning element

```php
public __clone(): mixed
```

***

### onClone

Method called after cloning on copying element

```php
protected onClone(): void
```

***

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

### renderElement

Render to base HTML element.

```php
public renderElement(): string
```

* This method is **abstract**.
***

### validateRequired

Validate if the control has a value if it's required.

```php
protected validateRequired(): bool
```

***

### validateMinMax

Validate if min and max for value.

```php
protected validateMinMax(): bool
```

***

### validateLength

Validate the length of the value.

```php
protected validateLength(): bool
```

***

### validatePattern

Validate the value of the control against a regex pattern.

```php
protected validatePattern(): bool
```

***

### validateMatch

Match value against another control.

```php
protected validateMatch(): bool
```

***

### validateUpload

Check if there were upload errors.

```php
protected validateUpload(): bool
```

***

### validateType

Validate if value matches the input type.

```php
protected validateType(): bool
```

***

### validateTypeColor

Validate the value for 'color' input type.

```php
protected validateTypeColor(): bool
```

***

### validateTypeNumber

Validate the value for 'number' input type.

```php
protected validateTypeNumber(): bool
```

***

### validateTypeRange

Validate the value for 'range' input type.

```php
protected validateTypeRange(): bool
```

***

### validateTypeDate

Validate the value for 'date' input type.

```php
protected validateTypeDate(): bool
```

***

### validateTypeDatetime

Validate the value for 'datetime' input type.

```php
protected validateTypeDatetime(): bool
```

***

### validateTypeDatetimeLocal

Validate the value for 'datetime' input type.

```php
protected validateTypeDatetimeLocal(): bool
```

***

### validateTypeTime

Validate the value for 'datetime' input type.

```php
protected validateTypeTime(): bool
```

***

### validateTypeMonth

Validate the value for 'month' input type.

```php
protected validateTypeMonth(): bool
```

***

### validateTypeWeek

Validate the value for 'week' input type.

```php
protected validateTypeWeek(): bool
```

***

### validateTypeUrl

Validate the value for 'url' input type.

```php
protected validateTypeUrl(): bool
```

***

### validateTypeEmail

Validate the value for 'email' input type.

```php
protected validateTypeEmail(): bool
```

***

### getValidationScript

Get JavaScript for custom validation.

```php
public getValidationScript(): string
```

***

### getValidationScriptRules

Get the rules to build up the validation script

```php
protected getValidationScriptRules(): array
```

***

### generateValidationScript

Generate validation script

```php
protected generateValidationScript(array $rules): string
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$rules`  | **array** |             |

***

### getValidationScriptMinlength

Get script to match the minimum length

```php
protected getValidationScriptMinlength(): string|null
```

***

### getValidationScriptMatch

Get script to match other element

```php
protected getValidationScriptMatch(): string|null
```

***

### parseForScript

Parse a message, inserting values for placeholders for JavaScript.

```php
public parseForScript(string $message): string
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$message` | **string** |             |

***

### resolvePlaceholderForScript

Get a value for a placeholder for JavaScript.

```php
protected resolvePlaceholderForScript(string $var): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$var`    | **string** |             |

***
