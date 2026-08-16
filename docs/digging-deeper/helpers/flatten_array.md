---
title: flatten_array
sidebar_title: flatten_array
description: Recursively flattens a multidimensional array into one level.
---

Description
-----------

Recursively flattens a multidimensional array into one level.

Usage
-----

```php
<?php

use function Qubus\Security\Helpers\flatten_array;

function flatten_array(array $array): array;
```

Parameters
----------

**$array** (array) (required) The multi-dimensional array to flatten.

Return Value
------------

(array) The flattened array.

Example
--------

```php
use function Qubus\Security\Helpers\flatten_array;

$flat = flatten_array(array: [
    'user' => [
        'name' => 'Ada',
        'roles' => ['admin', 'editor'],
    ],
    'active' => true,
]);

// ['name' => 'Ada', 0 => 'admin', 1 => 'editor', 'active' => true]
```

Parent keys are not retained. Numeric keys are re-indexed, and duplicate string keys encountered later can replace
earlier values.
