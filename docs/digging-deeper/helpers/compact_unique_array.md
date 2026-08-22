---
title: compact_unique_array
sidebar_title: compact_unique_array
summary: Remove duplicate and empty values from a PHP array with compact_unique_array and return a clean array of unique entries.
keywords: unique-array,array-cleanup,php-helper
---

Description
-----------

Strips out all duplicate values and compact the array.

Usage
-----

```php
<?php

use function Qubus\Support\Helpers\compact_unique_array;

function compact_unique_array(array $a): array;
```

Parameters
----------

**$a** (array) (required) An array to be compacted.

Return Value
------------

(bool) The unique array after its been compacted.
