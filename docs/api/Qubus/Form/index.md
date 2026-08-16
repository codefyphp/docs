
***

# Documentation



This is an automatically generated documentation for **Documentation**.

## Namespaces

### \Qubus\Form

#### Classes

| Class                                                | Description                       |
|------------------------------------------------------|-----------------------------------|
| [`Form`](./Form.md)               | Representation of an HTML <form>. |
| [`FormBuilder`](./FormBuilder.md) | FormBuilder factory               |
| [`FormView`](./FormView.md)       | Representation of an HTML <form>. |

### \Qubus\Form\FormBuilder

#### Classes

| Class                                                          | Description                                                       |
|----------------------------------------------------------------|-------------------------------------------------------------------|
| [`Action`](./FormBuilder/Action.md)         | Base class for a link or button.                                  |
| [`Attr`](./FormBuilder/Attr.md)             | HTML attributes                                                   |
| [`Button`](./FormBuilder/Button.md)         | Representation of an `button` element in a form.                  |
| [`Choice`](./FormBuilder/Choice.md)         | Representation of a control with items in a form.                 |
| [`ChoiceList`](./FormBuilder/ChoiceList.md) | Representation of a set of radio buttons or checkboxes in a form. |
| [`Control`](./FormBuilder/Control.md)       | Base class of form control elements.                              |
| [`Decorator`](./FormBuilder/Decorator.md)   | Decorator base class                                              |
| [`Div`](./FormBuilder/Div.md)               | Div element                                                       |
| [`Element`](./FormBuilder/Element.md)       | Base class for HTML elements.                                     |
| [`Fieldset`](./FormBuilder/Fieldset.md)     | Representation of an HTML `fieldset`.                             |
| [`FileInput`](./FormBuilder/FileInput.md)   | Base class of form control elements.                              |
| [`Group`](./FormBuilder/Group.md)           | Base class for an HTML element with children.                     |
| [`Hyperlink`](./FormBuilder/Hyperlink.md)   | Base class for a link or button.                                  |
| [`ImageInput`](./FormBuilder/ImageInput.md) | Base class of form control elements.                              |
| [`Input`](./FormBuilder/Input.md)           | Representation of an `input` element in a form.                   |
| [`Label`](./FormBuilder/Label.md)           | Div element                                                       |
| [`Legend`](./FormBuilder/Legend.md)         | Div element                                                       |
| [`Select`](./FormBuilder/Select.md)         | Representation of a `select` element.                             |
| [`Span`](./FormBuilder/Span.md)             | Div element                                                       |
| [`Textarea`](./FormBuilder/Textarea.md)     | Representation of a `textarea` element.                           |

#### Traits

| Trait                                                                    | Description                                                           |
|--------------------------------------------------------------------------|-----------------------------------------------------------------------|
| [`BasicValidation`](./FormBuilder/BasicValidation.md) | Basic input validation
 - Server side equivalent of HTML5 validation. |
| [`Components`](./FormBuilder/Components.md)           | Element that exists of several components.                            |

#### Interfaces

| Interface                                                              | Description                                |
|------------------------------------------------------------------------|--------------------------------------------|
| [`WithComponents`](./FormBuilder/WithComponents.md) | Element that exists of several components. |

### \Qubus\Form\FormBuilder\Decorator

#### Classes

| Class                                                                                | Description                 |
|--------------------------------------------------------------------------------------|-----------------------------|
| [`Bootstrap`](./FormBuilder/Decorator/Bootstrap.md)               | Decorator base class        |
| [`Dindent`](./FormBuilder/Decorator/Dindent.md)                   | Indent the HTML.            |
| [`SimpleFilter`](./FormBuilder/Decorator/SimpleFilter.md)         | Simple filter decorator     |
| [`SimpleValidation`](./FormBuilder/Decorator/SimpleValidation.md) | Simple validation decorator |
| [`Tidy`](./FormBuilder/Decorator/Tidy.md)                         | Tidy up the HTML.           |
