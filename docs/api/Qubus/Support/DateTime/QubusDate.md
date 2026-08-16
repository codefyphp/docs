# QubusDate

***

* Full name: `\Qubus\Support\DateTime\QubusDate`
* This class implements:
  [`\Qubus\Support\DateTime\Date`](./Date.md)

## Properties

### timezone

TimeZone

```php
public string|\DateTimeZone $timezone
```

***

### locale

Locale

```php
public ?string $locale
```

***

### date

Date object.

```php
public mixed $date
```

***

### time

```php
public string|int $time
```

***

## Methods

### __construct

Returns new Datetime object.

```php
private __construct(string|int $time, string|\DateTimeZone|null $timezone = null, ?string $locale = null): mixed
```

**Parameters:**

| Parameter   | Type                            | Description |
|-------------|---------------------------------|-------------|
| `$time`     | **string\|int**                 |             |
| `$timezone` | **string\|\DateTimeZone\|null** |             |
| `$locale`   | **?string**                     |             |

***

### fromString

```php
public static fromString(string|int $time, string|\DateTimeZone|null $timezone = null, ?string $locale = null): self
```

* This method is **static**.
**Parameters:**

| Parameter   | Type                            | Description |
|-------------|---------------------------------|-------------|
| `$time`     | **string\|int**                 |             |
| `$timezone` | **string\|\DateTimeZone\|null** |             |
| `$locale`   | **?string**                     |             |

***

### getDate

```php
public getDate(): mixed
```

***

### setTimezone

Sets the timezone.

```php
public setTimezone(string|\DateTimeZone $timezone): \DateTimeInterface
```

**Parameters:**

| Parameter   | Type                      | Description |
|-------------|---------------------------|-------------|
| `$timezone` | **string\|\DateTimeZone** |             |

***

### minuteInSeconds

Returns minute in seconds.

```php
public static minuteInSeconds(): int
```

* This method is **static**.
***

### hourInSeconds

Returns hour in seconds.

```php
public static hourInSeconds(): int
```

* This method is **static**.
***

### dayInSeconds

Returns day in seconds.

```php
public static dayInSeconds(): int
```

* This method is **static**.
***

### weekInSeconds

Returns week in seconds.

```php
public static weekInSeconds(): int
```

* This method is **static**.
***

### monthInSeconds

Returns month in seconds.

```php
public static monthInSeconds(): int
```

* This method is **static**.
***

### yearInSeconds

Returns year in seconds.

```php
public static yearInSeconds(): int
```

* This method is **static**.
***

### format

Formats date.

```php
public format(string $format = 'Y-m-d H:i:s'): string
```

This function uses the set timezone from TriTan options.

Example Usage:

     $datetime = 'May 15, 2018 2:15 PM';
     $this->format('Y-m-d H:i:s', $datetime);

**Parameters:**

| Parameter | Type       | Description                                   |
|-----------|------------|-----------------------------------------------|
| `$format` | **string** | Format of the date. Default is `Y-m-d H:i:s`. |

***

### gmtdate

Format a GMT/UTC date/time

```php
public gmtdate(string $date = 'now', string $format = 'Y-m-d H:i:s'): string
```

**Parameters:**

| Parameter | Type       | Description                                   |
|-----------|------------|-----------------------------------------------|
| `$date`   | **string** | Date to be formatted. Default is `now`.       |
| `$format` | **string** | Format of the date. Default is `Y-m-d H:i:s`. |

**Return Value:**

Formatted date string.

***

### locale

Returns the date in localized format.

```php
public locale(): \Carbon\Carbon|null
```

**Return Value:**

Returns current localized datetime.

***

### db2Date

Converts given date string into a different format.

```php
public db2Date(string $format, string $date, bool $translate = true): string|int|bool
```

$format should be either a PHP date format string, e.g. 'U' for a Unix
timestamp, or 'G' for a Unix timestamp assuming that $date is GMT.

If $translate is true, then the given date and format string will
be passed to $this->locale() for translation.

**Parameters:**

| Parameter    | Type       | Description                                                 |
|--------------|------------|-------------------------------------------------------------|
| `$format`    | **string** | Format of the date to return.                               |
| `$date`      | **string** | Date string to convert.                                     |
| `$translate` | **bool**   | Whether the return date should be translated. Default true. |

**Return Value:**

Formatted date string or Unix timestamp. False if $date is empty.

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
If $gmt is false, the output is adjusted with the GMT offset based on General Settings.

**Parameters:**

| Parameter | Type       | Description                                                                                  |
|-----------|------------|----------------------------------------------------------------------------------------------|
| `$type`   | **string** | Type of time to return. Accepts 'db', 'timestamp', or PHP date
format string (e.g. 'Y-m-d'). |
| `$gmt`    | **bool**   | Optional. Whether to use GMT timezone. Default false.                                        |

**Return Value:**

Integer if $type is 'timestamp', string otherwise.

***

### timestampToDate

Converts timestamp to localized human-readable date.

```php
public timestampToDate(string $format, int $timestamp): string
```

**Parameters:**

| Parameter    | Type       | Description                            |
|--------------|------------|----------------------------------------|
| `$format`    | **string** | PHP date format string (e.g. 'Y-m-d'). |
| `$timestamp` | **int**    | Timestamp to convert.                  |

**Return Value:**

Localized human readable date.

***

### timeAgo

Prints elapsed time based on datetime.

```php
public timeAgo(int $original): string
```

**Parameters:**

| Parameter   | Type    | Description |
|-------------|---------|-------------|
| `$original` | **int** |             |

***
