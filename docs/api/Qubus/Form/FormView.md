# FormView

Representation of an HTML <form>.

***

* Full name: `\Qubus\Form\FormView`
* Parent class: [`\Qubus\Form\Form`](./Form.md)
* This class is an **Abstract class**

## Properties

### opts

```php
protected array $opts
```

***

### attrs

```php
protected array $attrs
```

***

## Methods

### __construct

```php
public __construct(): mixed
```

***

### buildForm

```php
public buildForm(): \Qubus\Form\Form
```

* This method is **abstract**.
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
public addDecorator(string|\Qubus\Form\FormBuilder\Decorator $decorator): $this
```

**Parameters:**

| Parameter    | Type                                          | Description              |
|--------------|-----------------------------------------------|--------------------------|
| `$decorator` | **string\|\Qubus\Form\FormBuilder\Decorator** | Decorator object or name |

***

### applyDeepDecorators

Apply decorators from parent.

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

- [`TypeException`](../Exception/Data/TypeException.md)
- [`Exception`](../Exception/Exception.md)

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

- [`Exception`](../Exception/Exception.md)

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

Get unique identifier.

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

Validate the elements in the group.

```php
protected validate(): bool
```

***

### setContent

Set the element content.

```php
public setContent(\Closure|string|null $content = null): $this
```

**Parameters:**

| Parameter  | Type                       | Description |
|------------|----------------------------|-------------|
| `$content` | **\Closure\|string\|null** |             |

***

### getContent

Get the element content

```php
final public getContent(): string|null
```

* This method is **final**.
***

### renderContent

Render the content of the HTML element.

```php
protected renderContent(): string|null
```

***

### render

Render the child to HTML.

```php
protected render(): string
```

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

### add

Add a child to the group.

```php
public add(string|\Qubus\Form\FormBuilder\Element $child, array $options = [], array $attr = []): \Qubus\Form\FormBuilder\Group
```

**Parameters:**

| Parameter  | Type                                        | Description     |
|------------|---------------------------------------------|-----------------|
| `$child`   | **string\|\Qubus\Form\FormBuilder\Element** |                 |
| `$options` | **array**                                   | Element options |
| `$attr`    | **array**                                   | HTML attributes |

**Return Value:**

$this

**Throws:**

- [`Exception`](../Exception/Exception.md)

***

### begin

Add a child and return it.

```php
public begin(string|\Qubus\Form\FormBuilder\Element $child, array $options = [], array $attr = []): \Qubus\Form\FormBuilder\Element
```

**Parameters:**

| Parameter  | Type                                        | Description     |
|------------|---------------------------------------------|-----------------|
| `$child`   | **string\|\Qubus\Form\FormBuilder\Element** |                 |
| `$options` | **array**                                   | Element options |
| `$attr`    | **array**                                   | HTML attributes |

**Return Value:**

$child

**Throws:**

- [`\Qubus\Exception\Data\TypeException|\Qubus\Exception\Exception`](../Exception/Data/TypeException|/Qubus/Exception/Exception.md)

***

### getChildren

Get the children of the group.

```php
public getChildren(): array
```

***

### deepSearch

Find a specific child through deep search.

```php
protected deepSearch(\Qubus\Form\FormBuilder\Element|string $element, bool $unlink = false): \Qubus\Form\FormBuilder\Element|null
```

**Parameters:**

| Parameter  | Type                                        | Description              |
|------------|---------------------------------------------|--------------------------|
| `$element` | **\Qubus\Form\FormBuilder\Element\|string** | Element name or #id      |
| `$unlink`  | **bool**                                    | Unlink the found element |

***

### get

Get a specific child (deep search).

```php
public get(string $name): \Qubus\Form\FormBuilder\Element|null
```

**Parameters:**

| Parameter | Type       | Description         |
|-----------|------------|---------------------|
| `$name`   | **string** | Element name or #id |

***

### has

Checks if a specific child exists.

```php
public has(string $name): bool
```

**Parameters:**

| Parameter | Type       | Description         |
|-----------|------------|---------------------|
| `$name`   | **string** | Element name or id. |

***

### getControls

Get all the form elements in the group (deep search).

```php
public getControls(): \Qubus\Form\FormBuilder\Control[]
```

***

### remove

Remove a specific child (deep search)

```php
public remove(\Qubus\Form\FormBuilder\Element|string $element): \Qubus\Form\FormBuilder\Group
```

**Parameters:**

| Parameter  | Type                                        | Description                   |
|------------|---------------------------------------------|-------------------------------|
| `$element` | **\Qubus\Form\FormBuilder\Element\|string** | Element, element name or #id. |

**Return Value:**

$this

***

### setValues

Set the values of the elements.

```php
public setValues(array $values): \Qubus\Form\FormBuilder\Group
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$values` | **array** |             |

**Return Value:**

$this

***

### getValues

Get the values of the elements.

```php
public getValues(): array
```

***

### open

Render the opening tag

```php
public open(): string|null
```

***

### close

Render the closing tag

```php
public close(): string|null
```

***

### isSubmitted

Check if method matches and apply $_POST or $_GET parameters.

```php
public isSubmitted(bool $apply = true): bool
```

**Parameters:**

| Parameter | Type     | Description                                 |
|-----------|----------|---------------------------------------------|
| `$apply`  | **bool** | Set values using $_POST or $_GET parameters |

***
