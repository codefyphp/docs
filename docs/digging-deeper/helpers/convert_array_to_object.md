---
title: convert_array_to_object
sidebar_title: convert_array_to_object
summary: Convert an associative PHP array into an object with property access using the convert_array_to_object utility helper.
keywords: array-to-object,php-conversion,php-helper
---

Description
-----------

Takes an array and turns it into an object.

Usage
-----

```php
<?php

use function Qubus\Support\Helpers\convert_array_to_object;

function convert_array_to_object(array $array): object
```

Parameters
----------

**$array** (array) (required) An array of data.

Return Value
------------

(bool) The converted array that is now an object.
