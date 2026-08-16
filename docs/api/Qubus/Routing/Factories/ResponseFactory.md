# ResponseFactory

***

* Full name: `\Qubus\Routing\Factories\ResponseFactory`
* This class is marked as **final** and can't be subclassed
* This class implements:
  [`\Qubus\Routing\Factories\ResponsableFactory`](./ResponsableFactory.md)
* This class is a **Final class**

## Methods

### create

```php
public static create(\Psr\Http\Message\RequestInterface $request, string|\Psr\Http\Message\ResponseInterface|\Psr\Http\Message\StreamInterface|\Qubus\Routing\Interfaces\Responsable|null $response = ''): \Psr\Http\Message\ResponseInterface
```

* This method is **static**.
**Parameters:**

| Parameter   | Type                                                                                                                            | Description |
|-------------|---------------------------------------------------------------------------------------------------------------------------------|-------------|
| `$request`  | **\Psr\Http\Message\RequestInterface**                                                                                          |             |
| `$response` | **string\|\Psr\Http\Message\ResponseInterface\|\Psr\Http\Message\StreamInterface\|\Qubus\Routing\Interfaces\Responsable\|null** |             |

***
