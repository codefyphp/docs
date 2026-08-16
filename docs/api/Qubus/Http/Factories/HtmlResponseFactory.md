# HtmlResponseFactory

***

* Full name: `\Qubus\Http\Factories\HtmlResponseFactory`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Methods

### create

Create an HTML response.

```php
public static create(string|\Psr\Http\Message\StreamInterface $html, int $status = 200, array $headers = []): \Psr\Http\Message\ResponseInterface
```

Produces an HTML response with a Content-Type of text/html and a default
status of 200.

* This method is **static**.
**Parameters:**

| Parameter  | Type                                          | Description                                           |
|------------|-----------------------------------------------|-------------------------------------------------------|
| `$html`    | **string\|\Psr\Http\Message\StreamInterface** | HTML or stream for the message body.                  |
| `$status`  | **int**                                       | Integer status code for the response; 200 by default. |
| `$headers` | **array**                                     | Array of headers to use at initialization.            |

**Throws:**

If $html is neither a string or stream.
- [`\Exception|\InvalidArgumentException`](../../../Exception|/InvalidArgumentException.md)

***
