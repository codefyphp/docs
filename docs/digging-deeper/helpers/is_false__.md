---
title: is_false__
sidebar_title: is_false__
summary: Test whether a PHP value is strictly false with the is_false__ predicate helper and return a boolean result.
keywords: is-false,boolean-check,php-helper
---

Description
-----------

Checks if return is false.

Usage
-----

```php
<?php

use function Qubus\Support\Helpers\is_false__;

function is_false__(mixed $var): bool;
```

Parameters
----------

**$var** (mixed) (required) Variable to check.

Return Value
------------

(bool) Returns `true` if false, `false` otherwise.
