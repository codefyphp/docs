***

# RedirectResponseFactory





* Full name: `\Qubus\Http\Factories\RedirectResponseFactory`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**




## Methods


### create

Create a redirect response.

```php
public static create(string|\Psr\Http\Message\UriInterface $uri, int $status = 302, array $headers = []): \Psr\Http\Message\ResponseInterface
```

Produces a redirect response with a Location header and the given status
(302 by default).

Note: this method overwrites the `location` $headers value.

* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string&#124;\Psr\Http\Message\UriInterface** | URI for the Location header. |
| `$status` | **int** | Integer status code for the redirect; 302 by default. |
| `$headers` | **array** | Array of headers to use at initialization. |





***


***
> Automatically generated on 2025-10-13
