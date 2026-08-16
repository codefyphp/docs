---
title: strip_tags__
sidebar_title: strip_tags__
description: Removes complete HTML elements, including their contents.
---

Description
-----------

Removes complete HTML elements, including their contents. It always removes `script` and `style` blocks 
before applying the optional tag rules. This differs from PHP's `strip_tags()`, which normally retains text content.

Usage
-----

```php
<?php

use function Qubus\Security\Helpers\strip_tags__;

function strip_tags__(
    string $string,
    bool $removeBreaks = false,
    string $tags = '',
    bool $invert = false
): string;
```

Parameters
----------

**$string** (string) (required) String containing HTML tags.

**$removeBreaks** (bool) (optional) Whether to remove left over line breaks and white space chars.

**$tags** (string) (optional) Tags that should be removed.

**$invert** (bool) (optional) Instead of removing tags, this option checks for which tags to not remove.

Return Value
------------

(string) The processed string after the `strip_tags` filter has been applied.

Example
-------

```php
use function Qubus\Security\Helpers\strip_tags__;

$html = '<b>sample</b> text with <div>tags</div>';

strip_tags__(string: $html);
// ' text with '

strip_tags__(string: $html, removeBreaks: false, tags: '<b>');
// '<b>sample</b> text with '

strip_tags__(string: $html, removeBreaks: false, tags: '<b>', invert: true);
// ' text with <div>tags</div>'
```

When `$invert` is `false`, the `$tags` argument lists elements to keep. When `$invert` is `true`, it lists elements 
and contents to remove. The legacy `$removeBreaks` argument collapses remaining newlines, tabs, and repeated spaces 
only when execution reaches the function's final filtering branch; tag-selection branches return earlier.

This regular-expression utility is appropriate for removing known tag blocks; it is not a safe rich-text sanitizer 
or a complete HTML parser. Use [`purify_html()`](purify_html.md) for untrusted HTML that will be rendered.
