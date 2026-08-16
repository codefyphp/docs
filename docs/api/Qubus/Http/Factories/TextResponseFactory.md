# TextResponseFactory

***

* Full name: `\Qubus\Http\Factories\TextResponseFactory`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Methods

### create

Create a plain text response.

```php
public static create(string|\Psr\Http\Message\StreamInterface $text, int $status = 200, array $headers = []): \Psr\Http\Message\ResponseInterface
```

Produces a text response with a Content-Type of text/plain and a default
status of 200.

* This method is **static**.
**Parameters:**

| Parameter  | Type                                          | Description                                           |
|------------|-----------------------------------------------|-------------------------------------------------------|
| `$text`    | **string\|\Psr\Http\Message\StreamInterface** | String or stream for the message body.                |
| `$status`  | **int**                                       | Integer status code for the response; 200 by default. |
| `$headers` | **array**                                     | Array of headers to use at initialization.            |

**Throws:**

If $text is neither a string or stream.
- [`\Exception|\InvalidArgumentException`](../../../Exception|/InvalidArgumentException.md)

***
