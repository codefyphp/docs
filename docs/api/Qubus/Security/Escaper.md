***

# Escaper





* Full name: `\Qubus\Security\Escaper`
* This class implements:
[`\Qubus\Security\CleanHtmlEntities`](./CleanHtmlEntities.md)




## Methods


### htmlSpecialChars

Convert special characters to HTML entities

```php
private htmlSpecialChars(string $string, int $flags = ENT_QUOTES | ENT_HTML5, string $encoding = &#039;UTF-8&#039;, bool $doubleEncoding = true): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** | The string being converted. |
| `$flags` | **int** | A bitmask of one or more flags. |
| `$encoding` | **string** | An optional argument defining the encoding used when converting characters. |
| `$doubleEncoding` | **bool** | When double_encode is turned off PHP will not encode existing html entities,<br />the default is to convert everything. |




**Throws:**

- [`Exception`](../Exception/Exception.md)



***

### html

Escaping for HTML blocks.

```php
public html(string $string): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |


**Return Value:**

Escaped HTML block.



**Throws:**

- [`Exception`](../Exception/Exception.md)



***

### textarea

Escaping for textarea.

```php
public textarea(string $string): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |


**Return Value:**

Escaped string.



**Throws:**

- [`Exception`](../Exception/Exception.md)



***

### url

Escaping for url.

```php
public url(string $url, array $scheme = [], bool $encode = false): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$url` | **string** | The url to be escaped. |
| `$scheme` | **array** | The url scheme. |
| `$encode` | **bool** | Whether url params should be encoded. |


**Return Value:**

The escaped $url after the `escUrl` filter is applied.




***

### attr

Escaping for HTML attributes.

```php
public attr(string $string): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |


**Return Value:**

Escaped HTML attribute.



**Throws:**

- [`Exception`](../Exception/Exception.md)



***

### js

Escaping for inline javascript.

```php
public js(string $string): string
```

Example usage:

$esc_js = json_encode("Joshua's \"code\"");
$attribute = $this->js("alert($esc_js);");
echo '<input type="button" value="push" onclick="'.$attribute.'" />';






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |


**Return Value:**

Escaped inline javascript.



**Throws:**

- [`Exception`](../Exception/Exception.md)



***


***
> Automatically generated on 2025-10-13
