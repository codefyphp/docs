---
title: trim__
sidebar_title: trim__
---

Description
-----------

Despite its name, this helper removes all whitespace — not only whitespace at the beginning and end.

Usage
-----

```php
<?php

use function Qubus\Security\Helpers\trim__;

function trim__(array|string $string): array|string|null;
```

Parameters
----------

**$string** (array|string) (required) Array of string to be trimmed.

Return Value
------------

(array|string|null) The trimmed output.

Example
--------

It accepts either a string or an array of strings:

```php
use function Qubus\Security\Helpers\trim__;

$compact = trim__(string: " A value\nwith spaces\t");
// 'Avaluewithspaces'

$parts = trim__(string: ['first value', "second\nvalue"]);
// ['firstvalue', 'secondvalue']
```

Use PHP's native `trim()` when internal whitespace must be preserved.
