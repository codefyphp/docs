# FlashAware

***

* Full name: `\Qubus\Http\Session\FlashAware`

## Methods

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
