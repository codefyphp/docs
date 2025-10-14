***

# CleanHtmlEntities





* Full name: `\Qubus\Security\CleanHtmlEntities`



## Methods


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

The escaped $url after the `esc_url` filter is applied.




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




***

### js

Escaping for inline javascript.

```php
public js(string $string): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |


**Return Value:**

Escaped inline javascript.




***


***
> Automatically generated on 2025-10-13
