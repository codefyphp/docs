***

# RequestMethod





* Full name: `\Codefy\Framework\Support\RequestMethod`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`GET`|public| |&#039;GET&#039;|
|`POST`|public| |&#039;POST&#039;|
|`PUT`|public| |&#039;PUT&#039;|
|`DELETE`|public| |&#039;DELETE&#039;|
|`PATCH`|public| |&#039;PATCH&#039;|
|`HEAD`|public| |&#039;HEAD&#039;|
|`OPTIONS`|public| |&#039;OPTIONS&#039;|
|`CONNECT`|public| |&#039;CONNECT&#039;|
|`TRACE`|public| |&#039;TRACE&#039;|
|`ANY`|public| |[self::GET, self::POST, self::PUT, self::DELETE, self::PATCH, self::HEAD, self::OPTIONS, self::CONNECT, self::TRACE]|


## Methods


### isUnsafe

Checks if a given http method is not a safe method.

```php
public static isUnsafe(string $method): bool
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$method` | **string** |  |





***

### isSafe

Checks if a given http method is a safe method.

```php
public static isSafe(string $method): bool
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$method` | **string** |  |





***


***
> Automatically generated on 2025-10-13
