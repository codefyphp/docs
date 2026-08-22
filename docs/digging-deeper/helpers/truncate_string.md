---
title: truncate_string
sidebar_title: truncate_string
summary: Shorten plain text or HTML to a character limit, append a custom continuation marker, and optionally preserve markup with truncate_string.
keywords: truncate-string,text-shortening,php-helper
---

Description
-----------

Truncates a string to the given length. It will optionally preserve HTML tags if `$isHtml` is set to true.

Usage
-----

```php
<?php

use function Qubus\Support\Helpers\truncate_string;

function truncate_string(
    string $string,
    int $limit,
    string $continuation = '...',
    bool $isHtml = false
): string;
```

Parameters
----------

**$string** (string) (required) The string to truncate.

**$limit** (int) (required) The number of characters to truncate too.

**$continuation** (string) (optional) The string to use to denote it was truncated. Default ...

**$isHtml** (bool) (optional) Whether the string has HTML.

Return Value
------------

(bool) Returns `true` if true, `false` otherwise.
