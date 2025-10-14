***

# SessionData





* Full name: `\Qubus\Http\Session\SessionData`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Qubus\Http\Session\HttpSession`](./HttpSession.md)
* This class is a **Final class**



## Properties


### oldSessionId



```php
private string|null $oldSessionId
```






***

### objects



```php
private \Qubus\Http\Session\SessionEntity[] $objects
```






***

### clientSessionId



```php
private string $clientSessionId
```






***

### data



```php
private array $data
```






***

### isNew



```php
private bool $isNew
```






***

## Methods


### __construct



```php
public __construct(string $clientSessionId, array $data = [], bool $isNew = false): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$clientSessionId` | **string** |  |
| `$data` | **array** |  |
| `$isNew` | **bool** |  |





***

### sessionId

Returns the session's uuid which is derived
from the client session's id.

```php
public sessionId(): string
```











**Throws:**

- [`Exception`](../../../Exception.md)



***

### clientSessionId

Client session id which is stored in client's
cookie and never on the server.

```php
public clientSessionId(): string
```












***

### getData

Returns an array of object data.

```php
public getData(): array
```











**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)



***

### get

Retrieve session entity.

```php
public get(string $type): \Qubus\Http\Session\SessionEntity
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$type` | **string** | Fully qualified class name. |




**Throws:**

- [`\Qubus\Exception\Data\TypeException|\ReflectionException`](../../Exception/Data/TypeException|/ReflectionException.md)



***

### clear

Clear all session data, evict all objects from this Session, and renew {@see renew()}
the Session ID.

```php
public clear(): void
```











**Throws:**

- [`Exception`](../../../Exception.md)



***

### renew

Explicitly renew the Session ID while *preserving* any Session data.

```php
public renew(): void
```











**Throws:**

- [`Exception`](../../../Exception.md)



***

### isNew



```php
public isNew(): bool
```












***

### isRenewed



```php
public isRenewed(): bool
```












***

### oldSessionID



```php
public oldSessionID(): ?string
```












***

### checksum

Internally checksum a class implementation.

```php
protected checksum(string $type): string
```

Any change to the class source-file will cause invalidation of the session-model, such
that changes to the code will effectively cause session-models to re-initialize to their
default state - this is necessary because even a change to a type-hint in a doc-block
could cause an unserialize() call to inject the wrong type of value.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$type` | **string** | fully-qualified class-name |


**Return Value:**

MD5 checksum



**Throws:**

- [`ReflectionException`](../../../ReflectionException.md)



***


***
> Automatically generated on 2025-10-13
