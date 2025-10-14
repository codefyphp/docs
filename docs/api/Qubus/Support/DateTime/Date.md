***

# Date





* Full name: `\Qubus\Support\DateTime\Date`



## Methods


### format

Formats date.

```php
public format(string $format = &#039;Y-m-d H:i:s&#039;): string
```

This function uses the set timezone from date config.

Example Usage:

     $datetime = 'May 15, 2018 2:15 PM';
     $this->format('Y-m-d H:i:s', $datetime);






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$format` | **string** | Format of the date. Default is `Y-m-d H:i:s`. |





***

### current

Returns the current time based on specified type.

```php
public current(string $type, bool $gmt = false): int|string
```

The 'db' type will return the time in the format for database date field(s).
The 'timestamp' type will return the current timestamp.
Other strings will be interpreted as PHP date formats (e.g. 'Y-m-d H:i:s').

If $gmt is set to either '1' or 'true', then both types will use GMT time.
If $gmt is false, the output is adjusted with the GMT offset based on date config.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$type` | **string** | Type of time to return. Accepts &#039;db&#039;, &#039;timestamp&#039;, or PHP date<br />format string (e.g. &#039;Y-m-d&#039;). |
| `$gmt` | **bool** | Optional. Whether to use GMT timezone. Default false. |


**Return Value:**

Integer if $type is 'timestamp', string otherwise.




***


***
> Automatically generated on 2025-10-13
