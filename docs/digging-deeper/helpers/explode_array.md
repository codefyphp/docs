---
title: explode_array
sidebar_title: explode_array
description: Splits a string using one or more delimiters.
---


Description
-----------

Splits a string using one or more delimiters.

Usage
-----

```php
<?php

use function Qubus\Security\Helpers\explode_array;

function explode_array(array|string $delimiters, array|string $string): array;
```

Parameters
----------

**$delimiters** (array|string) (required) Delimiter(s) to search for.

**$string** (array|string) (required) String or array to be split.

Return Value
------------

(array)

## Example

It can also apply one delimiter to every string in an input array:

```php
use function Qubus\Security\Helpers\explode_array;

$colors = explode_array(delimiters: ',', string: 'red,green,blue');
// ['red', 'green', 'blue']

$tokens = explode_array(delimiters: [',', '|'], string: 'red,green|blue');
// ['red', 'green', 'blue']

$rows = explode_array(delimiters: ',', string: ['a,b', 'c,d']);
// ['a', 'b', 'c', 'd']
```

Supplying arrays for both arguments is not supported and returns an empty array. Empty delimiters should not be supplied.
