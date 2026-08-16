# ErrorBag

***

* Full name: `\Qubus\Validation\ErrorBag`

## Properties

### messages

```php
protected array $messages
```

***

## Methods

### __construct

Constructor

```php
public __construct(array $messages = []): void
```

**Parameters:**

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `$messages` | **array** |             |

***

### add

Add message for given key and rule

```php
public add(string $key, string $rule, string $message): void
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$key`     | **string** |             |
| `$rule`    | **string** |             |
| `$message` | **string** |             |

***

### count

Get messages count

```php
public count(): int
```

***

### has

Check given key is existed

```php
public has(string $key): bool
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### first

Get the first value of array

```php
public first(string $key): mixed
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### get

Get messages from given key, can be use custom format

```php
public get(string $key, string $format = ':message'): array
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |
| `$format` | **string** |             |

***

### all

Get all messages

```php
public all(string $format = ':message'): array
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$format` | **string** |             |

***

### firstOfAll

Get the first message from existing keys

```php
public firstOfAll(string $format = ':message', bool $dotNotation = false): array
```

**Parameters:**

| Parameter      | Type       | Description |
|----------------|------------|-------------|
| `$format`      | **string** |             |
| `$dotNotation` | **bool**   |             |

***

### toArray

Get plain array messages

```php
public toArray(): array
```

***

### parseKey

Parse $key to get the array of $key and $ruleName

```php
protected parseKey(string $key): array
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### isWildcardKey

Check the $key is wildcard

```php
protected isWildcardKey(mixed $key): bool
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$key`    | **mixed** |             |

***

### filterMessagesForWildcardKey

Filter messages with wildcard key

```php
protected filterMessagesForWildcardKey(string $key, mixed|null $ruleName = null): array
```

**Parameters:**

| Parameter   | Type            | Description |
|-------------|-----------------|-------------|
| `$key`      | **string**      |             |
| `$ruleName` | **mixed\|null** |             |

***

### formatMessage

Get formatted message

```php
protected formatMessage(string $message, string $format): string
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$message` | **string** |             |
| `$format`  | **string** |             |

***
