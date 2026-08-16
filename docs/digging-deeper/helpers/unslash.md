---
title: unslash
sidebar_title: unslash
description: Recursively remove backslashes from a string or nested array of strings.
---

Description
-----------

Recursively remove backslashes from a string or nested array of strings.

Usage
-----

```php
<?php

use function Qubus\Security\Helpers\unslash;

function unslash(mixed $value): array|string;
```

Return Value
------------

(string|array) The unslashed value.

Example
-------

```php
use function Qubus\Security\Helpers\unslash;

$input = [
    'name' => "O\\'Reilly",
    'quote' => '\\"Hello\\"',
];

$clean = unslash(value: $input);
// ['name' => "O'Reilly", 'quote' => '"Hello"']
```

The function does not sanitize HTML, SQL, paths, or shell input. Use them only when an API explicitly supplies or 
expects slash-escaped strings. Values should be strings or nested arrays of strings.
