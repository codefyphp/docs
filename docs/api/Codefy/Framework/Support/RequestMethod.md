# RequestMethod

***

* Full name: `\Codefy\Framework\Support\RequestMethod`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Constants

| Constant  | Visibility | Type | Value                                                                                                                |
|-----------|------------|------|----------------------------------------------------------------------------------------------------------------------|
| `GET`     | public     |      | 'GET'                                                                                                                |
| `POST`    | public     |      | 'POST'                                                                                                               |
| `PUT`     | public     |      | 'PUT'                                                                                                                |
| `DELETE`  | public     |      | 'DELETE'                                                                                                             |
| `PATCH`   | public     |      | 'PATCH'                                                                                                              |
| `HEAD`    | public     |      | 'HEAD'                                                                                                               |
| `OPTIONS` | public     |      | 'OPTIONS'                                                                                                            |
| `CONNECT` | public     |      | 'CONNECT'                                                                                                            |
| `TRACE`   | public     |      | 'TRACE'                                                                                                              |
| `ANY`     | public     |      | [self::GET, self::POST, self::PUT, self::DELETE, self::PATCH, self::HEAD, self::OPTIONS, self::CONNECT, self::TRACE] |

## Methods

### isUnsafe

Checks if a given http method is not a safe method.

```php
public static isUnsafe(string $method): bool
```

* This method is **static**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$method` | **string** |             |

***

### isSafe

Checks if a given http method is a safe method.

```php
public static isSafe(string $method): bool
```

* This method is **static**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$method` | **string** |             |

***
