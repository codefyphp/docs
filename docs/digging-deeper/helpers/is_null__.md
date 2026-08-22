---
title: is_null__
sidebar_title: is_null__
summary: Test whether a defined PHP variable contains null with the is_null__ predicate helper and return a boolean result.
keywords: is-null,null-check,php-helper
---

Description
-----------

Checks if a variable is null.

Works the same as PHP’s native `is_null()` function. If `$var` is not set, an `Undefined variable` notice will be thrown.

Usage
-----

```php
<?php

use function Qubus\Support\Helpers\is_null__;

function is_null__(mixed $var): bool;
```

Parameters
----------

**$var** (mixed) (required) Variable to check.

Return Value
------------

(bool) Returns `true` if null, `false` otherwise.
