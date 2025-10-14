***

# XmlResponseFactory





* Full name: `\Qubus\Http\Factories\XmlResponseFactory`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**




## Methods


### create

Create an XML response.

```php
public static create(string|\Psr\Http\Message\StreamInterface $xml, int $status = 200, array $headers = []): \Psr\Http\Message\ResponseInterface
```

Produces an XML response with a Content-Type of application/xml and a default
status of 200.

* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$xml` | **string&#124;\Psr\Http\Message\StreamInterface** | String or stream for the message body. |
| `$status` | **int** | Integer status code for the response; 200 by default. |
| `$headers` | **array** | Array of headers to use at initialization. |




**Throws:**
<p>If $text is neither a string or stream.</p>

- [`\Exception|\InvalidArgumentException`](../../../Exception|/InvalidArgumentException.md)



***


***
> Automatically generated on 2025-10-13
