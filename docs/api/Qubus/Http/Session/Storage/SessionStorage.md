# SessionStorage

The Session Storage abstraction defines a
contract for reading/writing/deleting raw Session Data.

***

* Full name: `\Qubus\Http\Session\Storage\SessionStorage`

## Methods

### read

Read raw Session Data from underlying storage.

```php
public read(string $sessionId): array|null
```

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$sessionId` | **string** |             |

***

### write

Write raw Session Data to underlying storage.

```php
public write(string $sessionId, array $data, int $ttl): void
```

**Parameters:**

| Parameter    | Type       | Description               |
|--------------|------------|---------------------------|
| `$sessionId` | **string** |                           |
| `$data`      | **array**  |                           |
| `$ttl`       | **int**    | time to live (in seconds) |

***

### destroy

Destroy the entire session by forcibly removing raw Session Data from underlying storage.

```php
public destroy(string $sessionId): void
```

Note that this differs substantially from 

- **See:** \Qubus\Http\Session\Storage\Session::clear(), which is the appropriate
way to clear the current user's session - the `destroy()` method is used internally to
flush empty sessions from storage, but may also be useful for (rare) use-cases, such as
forcibly destroying the active session of a blocked/banned user.

For actions such as users pressing a logout button, 
- **See:** \Qubus\Http\Session\Storage\Session::clear() is more appropriate.

**Parameters:**

| Parameter    | Type       | Description |
|--------------|------------|-------------|
| `$sessionId` | **string** |             |

***
