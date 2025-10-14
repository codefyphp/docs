***

# Emitter





* Full name: `\Qubus\Http\Emitter\Emitter`



## Methods


### emit

Emit a response.

```php
public emit(\Psr\Http\Message\ResponseInterface $response): void
```

Emits a response, including status line, headers, and the message body,
according to the environment.

Implementations of this method may be written in such a way as to have
side effects, such as usage of header() or pushing output to the
output buffer.

Implementations MAY raise exceptions if they are unable to emit the
response; e.g., if headers have already been sent.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$response` | **\Psr\Http\Message\ResponseInterface** |  |




**Throws:**

- [`EmitterException`](./Exceptions/EmitterException.md)



***


***
> Automatically generated on 2025-10-13
