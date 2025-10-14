***

# LogFormat





* Full name: `\Qubus\Log\LogFormat`
* This class implements:
[`\Qubus\Log\Format`](./Format.md)




## Methods


### create

Create the log format that will be used when writing to the file. It is
a template for the data: date/time, message, and an array.

```php
public create(string|\Psr\Log\LogLevel $level, string|\Stringable $message, array $context = []): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$level` | **string&#124;\Psr\Log\LogLevel** | PSR-3 log levels. |
| `$message` | **string&#124;\Stringable** | The log message to be written. |
| `$context` | **array** | An option array to be written to the log file. |


**Return Value:**

Return the string with the formatted log message.




***

### interpolate

Interpolate a string that contains braces as placeholders. It uses an associative
array as the key => value to replace the key (placeholder) with the value from the
array.

```php
protected interpolate(string $message, array $context = []): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$message` | **string** | The message containing the string that needs filtered |
| `$context` | **array** | An associative array of the key =&gt; value to interpolate |


**Return Value:**

The message after it has been interpolated.




***

### stringify



```php
protected stringify(array $data = []): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$data` | **array** |  |





***


***
> Automatically generated on 2025-10-13
