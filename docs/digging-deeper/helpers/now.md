---
title: now
sidebar_title: now
summary: Create a Carbon instance for the current date and time with an optional PHP time zone using the Qubus now helper.
keywords: carbon-datetime,php-timezone,now-helper
---

Description
-----------

Create a new Carbon instance for the current datetime.

Usage
-----

```php
<?php

use Carbon\Carbon;
use DateTimeZone;
use UnitEnum;

use function Qubus\Support\Helpers\now;

function now(DateTimeZone|UnitEnum|string|null $timezone = null): Carbon;
```

Parameters
----------

**$timezone** (DateTimeZone|UnitEnum|string|null) (optional) The permission to check for.

Return Value
------------

(string) The hidden input field.

Example
-------

```php
<?php

use function Qubus\Support\Helpers\now;

$now = now();
// or with timezone
$now = now('America/Los_Angeles');
```
