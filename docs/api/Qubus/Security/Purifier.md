***

# Purifier





* Full name: `\Qubus\Security\Purifier`



## Methods


### purify

Escaping for rich text.

```php
public purify(string $string, bool $isImage = false): string|bool|array
```

This method should only be used on output. With the exception of uploading
images, never use this method on input. All inputted data should be
accepted and then purified on output for optimal results.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** | The string to purify. |
| `$isImage` | **bool** | Is the string an image? |


**Return Value:**

Escaped rich text.




***


***
> Automatically generated on 2025-10-13
