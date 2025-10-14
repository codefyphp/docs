***

# Headers





* Full name: `\Qubus\Mail\Headers`



## Methods


### withSender

The envelope sender of the message.

```php
public withSender(string $sender = &#039;&#039;): static
```

This will usually be turned into a Return-Path header by the receiver,
and is the address that bounces will be sent to.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$sender` | **string** |  |





***

### withSubject

The Subject of the message.

```php
public withSubject(string $subject = &#039;&#039;): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$subject` | **string** |  |





***

### withPriority

Email priority.

```php
public withPriority(int|null $priority = null): static
```

Options: null (default), 1 = High, 3 = Normal, 5 = low.
When null, the header is not set at all.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$priority` | **int&#124;null** |  |





***

### withCharset

The character set of the message.

```php
public withCharset(string $charset = PHPMailer::CHARSET_ISO88591): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$charset` | **string** | The character set of the message. |





***

### withCustomHeader

Add a custom header.

```php
public withCustomHeader(string $name, string|null $value = null): static
```

$name value can be overloaded to contain
both header name and value (name:value).






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | Custom header name. |
| `$value` | **string&#124;null** | Header value. |




**Throws:**

- [`Exception`](../../PHPMailer/PHPMailer/Exception.md)



***

### withContentType

The MIME Content-type of the message.

```php
public withContentType(string $contentType = PHPMailer::CONTENT_TYPE_PLAINTEXT): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$contentType` | **string** |  |





***

### withXMailer

What to put in the X-Mailer header.

```php
public withXMailer(string|null $xmailer = &#039;&#039;): static
```

Options: An empty string for PHPMailer default,
whitespace/null for none, or a string to use.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$xmailer` | **string&#124;null** |  |





***


***
> Automatically generated on 2025-10-13
