---
title: concat_ws
sidebar_title: concat_ws
summary: Join two or more PHP strings with a configurable separator using the concat_ws helper for concise delimiter-based concatenation.
keywords: concat-ws,string-concatenation,php-helper
---

Description
-----------

Concatenation with separator.

Usage
-----

```php
<?php

use function Qubus\Support\Helpers\concat_ws;

function concat_ws(
    string $string1,
    string $string2,
    string $separator = ',',
    ...$strings
): string;
```

Parameters
----------

**$string1** (string) (required) Left string.

**$string2** (string (required) Right string.

**$separator** (string) (optional) Delimiter to use between strings. Default: comma.

**$…strings** (optional) List of strings.

Return Value
------------

(string) Concatenated string.

Example
-------

```php
echo concat_ws('CodefyPHP', 'Framework'); // "CodefyPHP,Framework"

echo concat_ws(
    'I love mangoes',
    'grapes',
    ', ',
    'pears',
    'and pineapple on pizza.'
); // "I love mangoes, grapes, pears, and pineapple on pizza."
```
