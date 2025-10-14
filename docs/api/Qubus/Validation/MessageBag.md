***

# MessageBag





* Full name: `\Qubus\Validation\MessageBag`
* This class implements:
[`\Countable`](../../Countable.md), [`\JsonSerializable`](../../JsonSerializable.md)



## Properties


### messages

All the registered messages.

```php
public array $messages
```






***

### format

Default format for message output.

```php
protected string $format
```






***

## Methods


### __construct

Create a new message bag instance.

```php
public __construct(array $messages = []): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$messages` | **array** |  |





***

### add

Add a message to the bag.

```php
public add(string $key, string $message): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |
| `$message` | **string** |  |





***

### merge

Merge a new array of messages into the bag.

```php
public merge(array $messages): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$messages` | **array** |  |





***

### isUnique

Determine if a key and message combination already exists.

```php
protected isUnique(string $key, string $message): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |
| `$message` | **string** |  |





***

### has

Determine if messages exist for a given key.

```php
public has(?string $key = null): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **?string** |  |





***

### first

Get the first message from the bag for a given key.

```php
public first(?string $key = null, ?string $format = null): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **?string** |  |
| `$format` | **?string** |  |





***

### get

Get all the messages from the bag for a given key.

```php
public get(string|null $key = null, string|null $format = null): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string&#124;null** |  |
| `$format` | **string&#124;null** |  |





***

### all

Get all the messages for every key in the bag.

```php
public all(string|null $format = null): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$format` | **string&#124;null** |  |





***

### transform

Format an array of messages.

```php
protected transform(array $messages, string $format, string $messageKey): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$messages` | **array** |  |
| `$format` | **string** |  |
| `$messageKey` | **string** |  |





***

### checkFormat

Get the appropriate format based on the given format.

```php
protected checkFormat(?string $format): ?string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$format` | **?string** |  |





***

### getMessageBag

Get the messages for the instance.

```php
public getMessageBag(): \Qubus\Validation\MessageBag
```












***

### getFormat

Get the default message format.

```php
public getFormat(): string
```












***

### setFormat

Set the default message format.

```php
public setFormat(string $format = &#039;:message&#039;): \Qubus\Validation\MessageBag
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$format` | **string** |  |





***

### isEmpty

Determine if the message bag has any messages.

```php
public isEmpty(): bool
```












***

### any

Determine if the message bag has any messages.

```php
public any(): bool
```












***

### count

Get the number of messages in the container.

```php
public count(): int
```












***

### toArray

Get the instance as an array.

```php
public toArray(): array
```












***

### jsonSerialize

Convert the object into something JSON serializable.

```php
public jsonSerialize(): array
```












***

### toJson

Convert the object to its JSON representation.

```php
public toJson(int $options): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$options` | **int** |  |





***

### __toString

Convert the message bag to its string representation.

```php
public __toString(): string
```












***


***
> Automatically generated on 2025-10-13
