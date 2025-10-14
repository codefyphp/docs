***

# LogFilename





* Full name: `\Qubus\Log\LogFilename`
* This class implements:
[`\Qubus\Log\Filename`](./Filename.md)




## Methods


### create

Create the log filename.

```php
public create(string|\Psr\Log\LogLevel $level, string $filenameFormat, string $filenameExtension): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$level` | **string&#124;\Psr\Log\LogLevel** | The log level. |
| `$filenameFormat` | **string** | Accepts the same parameters as PHP&#039;s date function. |
| `$filenameExtension` | **string** | Accepts a file extension such as log. |


**Return Value:**

The filename for the log file that will be written




***


***
> Automatically generated on 2025-10-13
