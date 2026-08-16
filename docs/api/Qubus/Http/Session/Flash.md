# Flash

***

* Full name: `\Qubus\Http\Session\Flash`

## Properties

### msgTypes

```php
protected array $msgTypes
```

***

### msgWrapper

```php
protected string $msgWrapper
```

***

### msgBefore

```php
protected string $msgBefore
```

***

### msgAfter

```php
protected string $msgAfter
```

***

### closeBtn

```php
protected string $closeBtn
```

***

### stickyCssClass

```php
protected string $stickyCssClass
```

***

### msgCssClass

```php
protected string $msgCssClass
```

***

### cssClassMap

```php
protected array $cssClassMap
```

***

### redirectUrl

```php
protected ?string $redirectUrl
```

***

### msgId

```php
public string $msgId
```

***

### session

```php
public \Qubus\Http\Session\PhpSession $session
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Http\Session\PhpSession $session): mixed
```

**Parameters:**

| Parameter  | Type                               | Description |
|------------|------------------------------------|-------------|
| `$session` | **\Qubus\Http\Session\PhpSession** |             |

**Throws:**

- [`SessionException`](./SessionException.md)

***

### notice

Notice messages.

```php
public notice(int $num): string
```

**Parameters:**

| Parameter | Type    | Description |
|-----------|---------|-------------|
| `$num`    | **int** |             |

***

### display

Display the flash messages

```php
public display(mixed|null $types = null, bool $print = true): bool|string
```

**Parameters:**

| Parameter | Type            | Description                                                                                                          |
|-----------|-----------------|----------------------------------------------------------------------------------------------------------------------|
| `$types`  | **mixed\|null** | (null)  print all of the message types
(array)  print the given message types
(string)   print a single message type |
| `$print`  | **bool**        | Whether to print the data or return it                                                                               |

***

### hasErrors

See if there are any queued error messages

```php
public hasErrors(): bool
```

***

### hasMessages

See if there are any queued message

```php
public hasMessages(string|null $type = null): bool
```

**Parameters:**

| Parameter | Type             | Description  |
|-----------|------------------|--------------|
| `$type`   | **string\|null** | The $msgType |

***

### formatMessage

Format a message

```php
protected formatMessage(array $msgDataArray, string $type): string
```

**Parameters:**

| Parameter       | Type       | Description           |
|-----------------|------------|-----------------------|
| `$msgDataArray` | **array**  | Array of message data |
| `$type`         | **string** | The $msgType          |

**Return Value:**

The formatted message

***

### doRedirect

Redirect the user if a URL was given.

```php
protected doRedirect(): \Psr\Http\Message\ResponseInterface|\Qubus\Http\Session\Flash
```

***

### clear

Clear the messages from the session data

```php
protected clear(mixed $types = []): \Qubus\Http\Session\Flash
```

**Parameters:**

| Parameter | Type      | Description                                                                                      |
|-----------|-----------|--------------------------------------------------------------------------------------------------|
| `$types`  | **mixed** | (array)   Clear all the message types in array.
(string)  Only clear the one given message type. |

***

### setMsgWrapper

Set the HTML that each message is wrapped in

```php
public setMsgWrapper(string $msgWrapper = ''): \Qubus\Http\Session\Flash
```

**Parameters:**

| Parameter     | Type       | Description                                                                                                                                        |
|---------------|------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| `$msgWrapper` | **string** | The HTML that each message is wrapped in.
Note: Two placeholders (%s) are expected.
The first is the $msgCssClass,
The second is the message text. |

***

### setMsgBefore

Prepend string to the message (inside of the message wrapper)

```php
public setMsgBefore(string $msgBefore = ''): \Qubus\Http\Session\Flash
```

**Parameters:**

| Parameter    | Type       | Description                      |
|--------------|------------|----------------------------------|
| `$msgBefore` | **string** | string to prepend to the message |

***

### setMsgAfter

Append string to the message (inside the message wrapper)

```php
public setMsgAfter(string $msgAfter = ''): \Qubus\Http\Session\Flash
```

**Parameters:**

| Parameter   | Type       | Description                     |
|-------------|------------|---------------------------------|
| `$msgAfter` | **string** | string to append to the message |

***

### setCloseBtn

Set the HTML for the close button

```php
public setCloseBtn(string $closeBtn = ''): \Qubus\Http\Session\Flash
```

**Parameters:**

| Parameter   | Type       | Description                      |
|-------------|------------|----------------------------------|
| `$closeBtn` | **string** | HTML to use for the close button |

***

### setStickyCssClass

Set the CSS class for sticky notes

```php
public setStickyCssClass(string $stickyCssClass = ''): \Qubus\Http\Session\Flash
```

**Parameters:**

| Parameter         | Type       | Description                              |
|-------------------|------------|------------------------------------------|
| `$stickyCssClass` | **string** | the CSS class to use for sticky messages |

***

### setMsgCssClass

Set the CSS class for messages

```php
public setMsgCssClass(string $msgCssClass = ''): \Qubus\Http\Session\Flash
```

**Parameters:**

| Parameter      | Type       | Description                       |
|----------------|------------|-----------------------------------|
| `$msgCssClass` | **string** | The CSS class to use for messages |

***

### setCssClassMap

Set the CSS classes for message types

```php
public setCssClassMap(mixed $msgType, mixed|null $cssClass = null): \Qubus\Http\Session\Flash
```

**Parameters:**

| Parameter   | Type            | Description                                                             |
|-------------|-----------------|-------------------------------------------------------------------------|
| `$msgType`  | **mixed**       | (string) The message type
(array) key/value pairs for the class map     |
| `$cssClass` | **mixed\|null** | (string) the CSS class to use
(null) not used when $msgType is an array |

***

## Inherited methods

### info

Add an info message

```php
public info(string $message, string|null $redirectUrl = null, bool $sticky = false): object
```

**Parameters:**

| Parameter      | Type             | Description                                 |
|----------------|------------------|---------------------------------------------|
| `$message`     | **string**       | The message text                            |
| `$redirectUrl` | **string\|null** | Where to redirect once the message is added |
| `$sticky`      | **bool**         | Sticky the message (hides the close button) |

***

### success

Add a success message

```php
public success(string $message, string|null $redirectUrl = null, bool $sticky = false): object
```

**Parameters:**

| Parameter      | Type             | Description                                 |
|----------------|------------------|---------------------------------------------|
| `$message`     | **string**       | The message text                            |
| `$redirectUrl` | **string\|null** | Where to redirect once the message is added |
| `$sticky`      | **bool**         | Sticky the message (hides the close button) |

***

### warning

Add a warning message

```php
public warning(string $message, string|null $redirectUrl = null, bool $sticky = false): object
```

**Parameters:**

| Parameter      | Type             | Description                                 |
|----------------|------------------|---------------------------------------------|
| `$message`     | **string**       | The message text                            |
| `$redirectUrl` | **string\|null** | Where to redirect once the message is added |
| `$sticky`      | **bool**         | Sticky the message (hides the close button) |

***

### error

Add an error message

```php
public error(string $message, string|null $redirectUrl = null, bool $sticky = false): object
```

**Parameters:**

| Parameter      | Type             | Description                                 |
|----------------|------------------|---------------------------------------------|
| `$message`     | **string**       | The message text                            |
| `$redirectUrl` | **string\|null** | Where to redirect once the message is added |
| `$sticky`      | **bool**         | Sticky the message (hides the close button) |

***

### sticky

Add a sticky message

```php
public sticky(string $message, string|null $redirectUrl = null, string $type = \Qubus\Http\Session\MessageType::DEFAULT): object
```

**Parameters:**

| Parameter      | Type             | Description                                 |
|----------------|------------------|---------------------------------------------|
| `$message`     | **string**       | The message text                            |
| `$redirectUrl` | **string\|null** | Where to redirect once the message is added |
| `$type`        | **string**       | The $msgType                                |

***

### add

Add a flash message to the session data

```php
public add(string $message, string $type = \Qubus\Http\Session\MessageType::DEFAULT, string|null $redirectUrl = null, bool $sticky = false): object|bool
```

**Parameters:**

| Parameter      | Type             | Description                                 |
|----------------|------------------|---------------------------------------------|
| `$message`     | **string**       | The message text                            |
| `$type`        | **string**       | The $msgType                                |
| `$redirectUrl` | **string\|null** | Where to redirect once the message is added |
| `$sticky`      | **bool**         | Whether the message is stickied             |

***
