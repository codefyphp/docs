***

# JsonResponseFactory





* Full name: `\Qubus\Http\Factories\JsonResponseFactory`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**




## Methods


### create

Create a JSON response with the given data.

```php
public static create(mixed $data, int $status = 200, array $headers = [], int $encodingOptions = 79): \Psr\Http\Message\ResponseInterface
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **mixed** | Data to convert to JSON. |
| `$status` | **int** | Integer status code for the response; 200 by default. |
| `$headers` | **array** | Array of headers to use at initialization. |
| `$encodingOptions` | **int** | JSON encoding options to use. |




**Throws:**
<p>If unable to encode the $data to JSON.</p>

- [`\Exception|\InvalidArgumentException`](../../../Exception|/InvalidArgumentException.md)



***


***
> Automatically generated on 2025-10-13
