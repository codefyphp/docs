***

# StringHelper





* Full name: `\Qubus\Support\StringHelper`




## Methods


### truncate

Truncates a string to the given length. It will optionally preserve
HTML tags if $isHtml is set to true.

```php
public truncate(string $string, int $limit, string $continuation = &#039;...&#039;, bool $isHtml = false): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** | The string to truncate. |
| `$limit` | **int** | The number of characters to truncate too. |
| `$continuation` | **string** | The string to use to denote it was truncated. |
| `$isHtml` | **bool** | Whether the string has HTML. |


**Return Value:**

The truncated string.




***

### increment

Adds _1 to a string or increment the ending number to allow _2, _3, etc

```php
public increment(string $str, int $first = 1, string $separator = &#039;_&#039;): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$str` | **string** | String to increment. |
| `$first` | **int** | Number that is used to mean first. |
| `$separator` | **string** | Separator between the name and the number. |





***

### startsWith

Checks whether a string has a specific beginning.

```php
public startsWith(string $str, string $start, bool $ignoreCase = false): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$str` | **string** | String to check. |
| `$start` | **string** | Beginning to check for. |
| `$ignoreCase` | **bool** | Whether to ignore the case. |


**Return Value:**

whether a string starts with a specified beginning.




***

### endsWith

Checks whether a string has a specific ending.

```php
public endsWith(string $str, string $end, bool $ignoreCase = false): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$str` | **string** | String to check. |
| `$end` | **string** | Ending to check for. |
| `$ignoreCase` | **bool** | Whether to ignore the case. |


**Return Value:**

Whether a string ends with a specified ending.




***

### random

Creates a random string of characters

```php
public random(string $type = &#039;alnum&#039;, int $length = 16): string|int|false
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$type` | **string** | The type of string. |
| `$length` | **int** | The number of characters. |


**Return Value:**

The random string.




***

### alternator

Returns a closure that will alternate between the args which to return.

```php
public alternator(): \Closure
```

If you call the closure with false as the arg it will return the value without
alternating the next time.










***

### tr

Parse the params from a string using strtr().

```php
public tr(string $string, array $array = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** | String to parse. |
| `$array` | **array** | Params to str_replace. |





***

### isJson

Check if a string is json encoded.

```php
public isJson(string $string): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** | String to check. |





***

### isXml

Check if a string is a valid XML.

```php
public isXml(string $string): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** | String to check. |




**Throws:**

- [`Exception`](../Exception/Exception.md)



***

### isSerialized

Check if a string is PHP serialized.

```php
public isSerialized(string $string): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** | String to check. |





***

### isHtml

Check if a string is html.

```php
public isHtml(string $string): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** | String to check. |





***

### strlen

Find the position of the first occurrence of a substring in a string.

```php
public strlen(string $str, string|null $encoding = &#039;UTF-8&#039;): int|false
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$str` | **string** | The string being measured for length. |
| `$encoding` | **string&#124;null** | Defaults to the setting in the config, which defaults to UTF-8. |


**Return Value:**

The length of the string on success, and 0 if the string is empty.




***

### strpos

Find position of first occurrence of string in a string.

```php
public strpos(string $haystack, mixed $needle, int $offset, string|null $encoding = &#039;UTF-8&#039;): false|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$haystack` | **string** | The string being checked. |
| `$needle` | **mixed** | The string to find in haystack. |
| `$offset` | **int** | The search offset. |
| `$encoding` | **string&#124;null** |  |


**Return Value:**

Returns the position of where the needle exists relative to the beginning
of the haystack string (independent of offset). Also note that string
positions start at 0, and not 1.
Returns false if the needle was not found.




***

### strrpos

Find position of last occurrence of a string in a string.

```php
public strrpos(string $haystack, mixed $needle, int $offset): false|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$haystack` | **string** | The string being checked. |
| `$needle` | **mixed** | The string to find in haystack. |
| `$offset` | **int** | The search offset. |


**Return Value:**

Returns the numeric position of the last occurrence of needle in the
haystack string. If needle is not found, it returns false.




***

### substr

Get part of string.

```php
public substr(string $str, int $start, int|null $length = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$str` | **string** | The string to extract the substring from. |
| `$start` | **int** | If start is non-negative, the returned string will start at the start&#039;th<br />position in str, counting from zero. If start is negative, the returned<br />string will start at the start&#039;th character from the end of str. |
| `$length` | **int&#124;null** | Maximum number of characters to use from str. If omitted or NULL is passed,<br />extract all characters to the end of the string. |


**Return Value:**

Returns the extracted part of string; or false on failure, or an empty string.




***

### strtolower

Make a string lowercase.

```php
public strtolower(string $str): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$str` | **string** | The string to convert to lowercase. |


**Return Value:**

The lowercase string.




***

### strtoupper

Make a string uppercase.

```php
public strtoupper(string $str): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$str` | **string** | The string to convert to uppercase. |


**Return Value:**

The uppercase string.




***

### stripos

Find the position of the first occurrence of a case-insensitive substring in a string.

```php
public stripos(string $haystack, string $needle, int $offset): false|int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$haystack` | **string** | The string from which to get the position of the last occurrence of needle. |
| `$needle` | **string** | The string to find in haystack. |
| `$offset` | **int** | The search offset. |


**Return Value:**

Returns the position of where the needle exists relative to the beginning
of the haystack string (independent of offset). Also note that string
positions start at 0, and not 1.
Returns false if the needle was not found.




***

### strripos

Finds position of last occurrence of a string within another, case insensitive.

```php
public strripos(string $haystack, string $needle, int $offset): int|bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$haystack` | **string** | The string from which to get the position of the last occurrence of needle. |
| `$needle` | **string** | The string to find in haystack. |
| `$offset` | **int** | The search offset. |


**Return Value:**

Returns the numeric position of the last occurrence of needle in the
haystack string. If needle is not found, it returns false.




***

### strstr

Finds first occurrence of a string within another.

```php
public strstr(string $haystack, string $needle, bool $beforeNeedle = false): string|bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$haystack` | **string** | The string from which to get the position of the last occurrence of needle. |
| `$needle` | **string** | The string to find in haystack. |
| `$beforeNeedle` | **bool** | Determines which portion of haystack this function returns. |


**Return Value:**

The portion of haystack, or false if needle is not found.




***

### stristr

Finds first occurrence of a string within another, case-insensitive.

```php
public stristr(string $haystack, string $needle, bool $beforeNeedle = false): string|bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$haystack` | **string** | The string from which to get the position of the last occurrence of needle. |
| `$needle` | **string** | The string to find in haystack. |
| `$beforeNeedle` | **bool** | Determines which portion of haystack this function returns. |


**Return Value:**

The portion of haystack, or false if needle is not found.




***

### strrchr

Finds the last occurrence of a character in a string within another.

```php
public strrchr(string $haystack, string $needle, bool $beforeNeedle = false): false|string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$haystack` | **string** | The string from which to get the last occurrence of needle. |
| `$needle` | **string** | The string to find in haystack. |
| `$beforeNeedle` | **bool** |  |


**Return Value:**

The portion of haystack, or false if needle is not found.




***

### substrCount

substr_count — Count the number of substring occurrences.

```php
public substrCount(string $haystack, string $needle, int $offset): int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$haystack` | **string** | The string from which to get the position of the last occurrence of needle. |
| `$needle` | **string** | The string to find in haystack. |
| `$offset` | **int** | The search offset. |


**Return Value:**

The number of occurrences found.




***

### lcfirst

Does not strtoupper first.

```php
public lcfirst(string $str): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$str` | **string** | String to lowercase first letter. |





***

### ucfirst

Does not strtolower first.

```php
public ucfirst(string $str): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$str` | **string** | String to uppercase first letter. |





***

### ucwords

First strtolower then ucwords.

```php
public ucwords(string $str): string
```

ucwords normally doesn't strtolower first
but MB_CASE_TITLE does, so ucwords now too.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$str` | **string** | String to uppercase. |





***


***
> Automatically generated on 2025-10-13
