---
title: esc_attr
sidebar_title: esc_attr
summary: Escape untrusted PHP values for safe insertion into quoted HTML attributes and prevent markup from breaking the attribute context.
keywords: html-attribute-escaping,xss-prevention,php-security
description: Escapes an ordinary value for a quoted HTML attribute.
---

Description
-----------

Escapes an ordinary value for a quoted HTML attribute.

Usage
-----

```php
<?php

use function Qubus\Security\Helpers\esc_attr;

function esc_attr(string $string): string;
```

Parameters
----------

**$string** (string) (required) Attribute to be escaped.

Return Value
------------

(string) Escaped HTML attribute after the `esc_attr` filter has been applied.

Example
---------

```php
$label = 'Save "draft" <now>';

echo '<button title="' . esc_attr(string: $label) . '">Save</button>';
// <button title="Save &quot;draft&quot; &lt;now&gt;">Save</button>
```

Always quote the surrounding attribute. This helper does not validate URL, CSS, JavaScript, or `srcdoc` attributes.
