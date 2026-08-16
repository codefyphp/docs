# HttpSession

***

* Full name: `\Qubus\Http\Session\HttpSession`

## Constants


| Constant      | Visibility | Type | Value        |
|---------------|------------|------|--------------|
| `COOKIE_NAME` | public     |      | "HTTPSESSID" |

## Methods

### get

Retrieve session entity.

```php
public get(string $type): \Qubus\Http\Session\SessionEntity
```

**Parameters:**

| Parameter | Type       | Description                 |
|-----------|------------|-----------------------------|
| `$type`   | **string** | Fully qualified class name. |

**Throws:**

Class name given does not exist.
- [`TypeException`](../../Exception/Data/TypeException.md)

***

### getData

Returns an array of object data.

```php
public getData(): array
```

***

### clear

Clear all session data, evict all objects from this Session, and renew {@see renew()}
the Session ID.

```php
public clear(): void
```

Note that references to any session entity objects obtained via `get()` during the
same request will be *orphaned* from this Session - they will *not* be committed
to session state at the end of the request.

(This is not as bad as it may sound, as very likely the only practical use-case for
`clear()` is a logout controller/action, during which likely no other session models
would be used or manipulated.)

***

### renew

Explicitly renew the Session ID while *preserving* any Session data.

```php
public renew(): void
```

The likely use-case is a login controller/action, where issuing a new Session ID,
while invalidating the previous Session ID, can provide an extra measure of security,
e.g. by avoiding very long-lived valid Session IDs.

Note that periodic renewal of the Session ID is *not* recommended - issuing a new
Session ID should be done only after authentication, e.g. after successful validation
of user-supplied login credentials over a secure connection.

***

### sessionId

Returns the session's uuid which is derived
from the client session's id.

```php
public sessionId(): string
```

***

### clientSessionId

Client session id which is stored in client's
cookie and never on the server.

```php
public clientSessionId(): string
```

***
