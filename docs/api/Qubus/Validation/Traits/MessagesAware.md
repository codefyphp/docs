# MessagesAware

***

* Full name: `\Qubus\Validation\Traits\MessagesAware`

## Properties

### messages

```php
protected array $messages
```

***

## Methods

### setMessage

Given $key and $message to set message.

```php
public setMessage(mixed $key, mixed $message): void
```

**Parameters:**

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `$key`     | **mixed** |             |
| `$message` | **mixed** |             |

***
### setMessages

Given $messages and set multiple messages.

```php
public setMessages(array $messages): void
```

**Parameters:**

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `$messages` | **array** |             |

***
### getMessage

Given message from given $key.

```php
public getMessage(string $key): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***
### getMessages

Get all $messages

```php
public getMessages(): array
```

***
