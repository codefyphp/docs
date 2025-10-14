***

# Addresses





* Full name: `\Qubus\Mail\Addresses`



## Methods


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


***
> Automatically generated on 2025-10-13
