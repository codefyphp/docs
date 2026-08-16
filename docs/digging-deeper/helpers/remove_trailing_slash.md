---
title: remove_trailing_slash
sidebar_title: remove_trailing_slash
---

Description
-----------

Removes trailing forward slashes and backslashes if they exist.

Usage
-----

```php
<?php

use function Qubus\Support\Helpers\remove_trailing_slash;

function remove_trailing_slash(string $string): string;
```

Parameters
----------

**$string** (string) (required) What to remove the trailing slashes from.

Return Value
------------

(string) String without the trailing slash.
