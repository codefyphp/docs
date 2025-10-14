***

# Mailer





* Full name: `\Qubus\Mail\Mailer`
* Parent interfaces: [`\Qubus\Mail\Headers`](./Headers.md), [`\Qubus\Mail\Addresses`](./Addresses.md), [`\Qubus\Mail\Transport`](./Transport.md)


## Methods


### withHtml

Sets message type to HTML or plaintext.

```php
public withHtml(bool $isHtml = false): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$isHtml` | **bool** | True for HTML mode. |





***

### withAttachment

Add an attachment from a path on the filesystem.

```php
public withAttachment(string $path, string $name = &#039;&#039;, string $encode = PHPMailer::ENCODING_BASE64, string $type = &#039;&#039;, string $disposition = &#039;attachment&#039;): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **string** | Path to the attachment |
| `$name` | **string** | Overrides the attachment name |
| `$encode` | **string** | File encoding (see $Encoding) |
| `$type` | **string** | MIME type, e.g. `image/jpeg`; determined automatically from $path if not specified |
| `$disposition` | **string** | Disposition to use. |




**Throws:**

- [`Exception`](../../PHPMailer/PHPMailer/Exception.md)



***

### withBody

Set Mail Body configuration

```php
public withBody(array|string $data, array $options = []): static
```

Format email message Body, this can be an external template html file with a copy
of a plain-text like template.txt or HTML/plain-text string.

This method can be used by passing a template file HTML name and an associative array
with the values that can be parsed into the file HTML by the key KEY_NAME found in your
array to your HTML {{KEY_NAME}}.

Other optional ways to format the mail body is available like instead of a template the
param $data can be set as an array or string, but param $options['template_name'] must be equal to null.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array&#124;string** | Contain the values to be parsed in mail body. |
| `$options` | **array** | Array of options. |





***

### withAltBody

The plain-text message body.

```php
public withAltBody(string $message = &#039;&#039;): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** |  |





***

### save

Save message as eml file.

```php
public save(): bool
```









**Return Value:**

True if saved successfully, false otherwise.



**Throws:**

- [`Exception`](../Exception/Exception.md)



***

### send

Create a message and send it.

```php
public send(): bool
```

Uses the sending method specified by $Mailer.







**Return Value:**

false on error.



**Throws:**

- [`\PHPMailer\PHPMailer\Exception|\Qubus\Exception\Exception`](../../PHPMailer/PHPMailer/Exception|/Qubus/Exception/Exception.md)



***


## Inherited methods


### withSmtp

Send messages using SMTP.

```php
public withSmtp(): static
```











**Throws:**

- [`Exception`](../Exception/Exception.md)



***

### withMail

Send messages using PHP's native mail() function.

```php
public withMail(): static
```












***

### withSendmail

Send messages using Sendmail.

```php
public withSendmail(): static
```












***

### withQmail

Send messages using qmail.

```php
public withQmail(): static
```












***

### withFrom

Set the From and FromName properties.

```php
public withFrom(string $address, string $name = &#039;&#039;, bool $auto = true): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$address` | **string** |  |
| `$name` | **string** |  |
| `$auto` | **bool** | Whether to also set the Sender address, defaults to true. |




**Throws:**

- [`Exception`](../../PHPMailer/PHPMailer/Exception.md)



***

### withTo

Add a "To" address.

```php
public withTo(string|array $address): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$address` | **string&#124;array** | The email address(es) to send to. |




**Throws:**

- [`Exception`](../../PHPMailer/PHPMailer/Exception.md)



***

### withCc

Add a "CC" address.

```php
public withCc(string|array $address): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$address` | **string&#124;array** | The email address(es) to send to. |




**Throws:**

- [`Exception`](../../PHPMailer/PHPMailer/Exception.md)



***

### withBcc

Add a "BCC" address.

```php
public withBcc(string|array $address): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$address` | **string&#124;array** | The email address(es) to send to. |




**Throws:**

- [`Exception`](../../PHPMailer/PHPMailer/Exception.md)



***

### withReplyTo

Add a "Reply-To" address.

```php
public withReplyTo(string|array $address): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$address` | **string&#124;array** | The email address(es) to reply to. |




**Throws:**

- [`Exception`](../../PHPMailer/PHPMailer/Exception.md)



***

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
