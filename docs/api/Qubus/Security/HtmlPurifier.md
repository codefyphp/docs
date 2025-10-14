***

# HtmlPurifier





* Full name: `\Qubus\Security\HtmlPurifier`
* This class implements:
[`\Qubus\Security\Purifier`](./Purifier.md)



## Properties


### neverAllowedStr



```php
protected array $neverAllowedStr
```






***

### neverAllowedRegex

List of never allowed regex replacement

```php
protected array $neverAllowedRegex
```






***

### xssDisalowedAttibutes

Remove bad attributes such as style, onclick and xmlns

```php
public array $xssDisalowedAttibutes
```






***

### xssNaughtyHtml

If a tag containing any of the words in the list below is found,
the tag gets converted to entities.

```php
public string $xssNaughtyHtml
```






***

### xssNaughtyScripts

Similar to $this->xssNaughtyHtml, but instead of looking for tags it
looks for PHP and JavaScript commands that are disallowed.  Rather than
removing the code, it simply converts the parenthesis to entities
rendering the code un-executable.

```php
public string $xssNaughtyScripts
```






***

### filenameBadChars

List of sanitize filename strings.

```php
public array $filenameBadChars
```






***

### mbencoding

Your mb_string encoding, default is 'utf-8'. Do not change, if not sure.

```php
public string $mbencoding
```






***

## Methods


### __construct



```php
public __construct(): mixed
```












***

### purify

Escaping for rich text.

```php
public purify(string|string[] $string, bool $isImage = false): string|bool|array
```

This method should only be used on output. With the exception of uploading
images, never use this method on input. All inputted data should be
accepted and then purified on output for optimal results. For output of images,
make sure to escape with esc_url().






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string&#124;string[]** | The string to purify. |
| `$isImage` | **bool** | Is the string an image? |


**Return Value:**

Escaped rich text.




***

### entityDecode

HTML Entities Decode

```php
public entityDecode(string $string, string $charset = &#039;UTF-8&#039;): string
```

This function is a replacement for html_entity_decode()

The reason we are not using html_entity_decode() by itself is because
while it is not technically correct to leave out the semicolon
at the end of an entity most browsers will still interpret the entity
correctly.  html_entity_decode() does not convert entities without
semicolons, so we are left with our own little solution here. Bummer.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |
| `$charset` | **string** |  |


**Return Value:**

The decoded string.




***

### urlDecodeSpaces

URL-decode taking spaces into account

```php
protected urlDecodeSpaces(array $matches): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$matches` | **array** |  |





***

### compactExplodedWords

Compact Exploded Words

```php
protected compactExplodedWords(array $matches): string
```

Callback function for $this->purify() to remove whitespace from
things like j a v a s c r i p t.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$matches` | **array** |  |





***

### removeEvilAttributes

Remove evil HTML Attributes (like evenhandlers and style)

```php
protected removeEvilAttributes(string $string, bool $isImage): string
```

It removes the evil attribute and either:

- Everything up until a space
   For example, everything between the pipes:
   <a |style=document.write('hello');alert('world');| class=link>

 - Everything inside the quotes
   For example, everything between the pipes:
   <a |style="document.write('hello'); alert('world');"| class="link">






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** | The string to check |
| `$isImage` | **bool** | true if this is an image |


**Return Value:**

The string with the evil attributes removed




***

### sanitizeNaughtyHtml

Sanitize Naughty HTML

```php
protected sanitizeNaughtyHtml(array $matches): string
```

Callback function for $this->purify() to sanitize naughty HTML elements.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$matches` | **array** |  |





***

### jsLinkRemoval

JS Link Removal

```php
protected jsLinkRemoval(array $match): string
```

Callback function for $this->purify() to sanitize links. This limits the PCRE backtracks,
making it more performant friendly.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$match` | **array** |  |





***

### jsImgRemoval

JS Image Removal

```php
protected jsImgRemoval(array $match): string
```

Callback function for $this->purify() to sanitize image tags. This limits the PCRE backtracks,
making it more performance friendly.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$match` | **array** |  |





***

### convertAttribute

Attribute Conversion

```php
protected convertAttribute(array $match): string
```

Used as a callback for Purify.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$match` | **array** |  |





***

### filterAttributes

Filter Attributes

```php
protected filterAttributes(string $string): string
```

Filters tag attributes for consistency and safety.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |





***

### decodeEntity

HTML Entity Decode Callback

```php
protected decodeEntity(array $match): string
```

Used as a callback for Purify.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$match` | **array** |  |





***

### validateEntities

Validate URL entities

```php
protected validateEntities(string $string): string
```

Called by $this->purify().






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |





***

### neverAllowed

Never Allowed

```php
protected neverAllowed(string $string): string
```

A utility function for $this->purify().






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |





***

### removeInvisibleCharacters

Removes invisible characters.

```php
protected removeInvisibleCharacters(string $string, bool $urlEncoded = true): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |
| `$urlEncoded` | **bool** |  |





***

### sanitizeFilename

Sanitize Filename

```php
public sanitizeFilename(string $string, bool $relativePath = false): string
```

Tries to sanitize filenames in order to prevent directory traversal attempts
and other security threats, which is particularly useful for files that
were supplied via user input.

If it is acceptable for the user input to include relative paths,
e.g. file/in/some/approved/folder.txt, you can set the second optional
parameter, $relativePath to true.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** | Input file name |
| `$relativePath` | **bool** | Whether to preserve paths |





***


***
> Automatically generated on 2025-10-13
