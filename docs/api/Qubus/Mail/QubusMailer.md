***

# QubusMailer





* Full name: `\Qubus\Mail\QubusMailer`
* Parent class: [`PHPMailer`](../../PHPMailer/PHPMailer/PHPMailer.md)
* This class implements:
[`\Qubus\Mail\Mailer`](./Mailer.md)



## Properties


### templatePath



```php
protected ?string $templatePath
```






***

### config



```php
protected \Qubus\Config\ConfigContainer $config
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Config\ConfigContainer $config): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$config` | **\Qubus\Config\ConfigContainer** |  |





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





***

### withAddresses



```php
private withAddresses(string $type, mixed $addresses): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$type` | **string** | Type of the recipient (to, cc, bcc or Reply-To) |
| `$addresses` | **mixed** | Email address or array of email addresses. |


**Return Value:**

True on success, false if addresses not valid.



**Throws:**

- [`Exception`](../../PHPMailer/PHPMailer/Exception.md)



***

### withSender

The envelope sender of the message.

```php
public withSender(string $sender = &#039;&#039;): static
```








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

### withPriority

Email priority.

```php
public withPriority(?int $priority = null): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$priority` | **?int** |  |





***

### withCharset

The character set of the message.

```php
public withCharset(string $charset = self::CHARSET_ISO88591): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$charset` | **string** | The character set of the message. |





***

### withCustomHeader

Add a custom header.

```php
public withCustomHeader(string $name, ?string $value = null): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | Custom header name. |
| `$value` | **?string** | Header value. |





***

### withContentType

The MIME Content-type of the message.

```php
public withContentType(string $contentType = self::CONTENT_TYPE_PLAINTEXT): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$contentType` | **string** |  |





***

### withAttachment

Add an attachment from a path on the filesystem.

```php
public withAttachment(string $path, string $name = &#039;&#039;, string $encode = self::ENCODING_BASE64, string $type = &#039;&#039;, string $disposition = &#039;attachment&#039;): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **string** | Path to the attachment |
| `$name` | **string** | Overrides the attachment name |
| `$encode` | **string** | File encoding (see $Encoding) |
| `$type` | **string** | MIME type, e.g. `image/jpeg`; determined automatically from $path if not specified |
| `$disposition` | **string** | Disposition to use. |





***

### withBody

Set Mail Body configuration

```php
public withBody(string|array $data, array $options = []): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **string&#124;array** | Contain the values to be parsed in mail body. |
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

### withXMailer

What to put in the X-Mailer header.

```php
public withXMailer(?string $xmailer = &#039;&#039;): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$xmailer` | **?string** |  |





***

### withSmtp

Send messages using SMTP.

```php
public withSmtp(): static
```












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

### save

Save message as eml file.

```php
public save(): bool
```









**Return Value:**

True if saved successfully, false otherwise.




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


***
> Automatically generated on 2025-10-13
