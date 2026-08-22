---
title: array_list
sidebar_title: array_list
summary: Create a Qubus ArrayList collection that enforces the expected type of every value for safer, consistent PHP array operations.
keywords: array-list,typed-collection,php-helper
---

Description
-----------

Return a collection based on type.

Usage
-----

```php
<?php

use Qubus\Support\Collection\ArrayList;

use function Qubus\Support\Helpers\array_list;

function array_list(string $type): ArrayList;
```

Parameters
----------

**$type** (string) (required) The type of array values expected.

Return Value
------------

(string) A collection.

Example
-------

```php
<?php

use function Qubus\Support\Helpers\array_list;

$callables = [
    fn() => 'Hello World!',
    fn() => 'I love programming!',
    fn() => 'I love PHP!'
];

$list = array_list('callable');
foreach ($callables as $callable) {
    $list->add($callable);
}

echo $list->type(); // callable
// or
echo $list->all()[2](); // I love PHP!
```

Go Further
----------

To use the `array_list()` helper beyond the example above, check out [`Collections`](../collections.md). 
The `array_list()` helper and the `collect()` helper inherit some of the same methods but may return different results. 
Another difference is that `collect()` can return a mixture of primitives and data structures, while `array_list()` 
returns an array of the same specified primitive type.
