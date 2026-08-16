---
title: esc_html
sidebar_title: esc_html
description: Escapes plain text that will be placed between HTML tags.
---

Description
-----------

Escapes plain text that will be placed between HTML tags.

Usage
-----

```php
<?php

use function Qubus\Security\Helpers\esc_html;

function esc_html(string $string): string;
```

Parameters
----------

**$string** (string) (required) Html element to escape.

Return Value
------------

(string) Escaped HTML output.

Example
----------

Markup in the value is displayed as text rather than interpreted by the browser:

```php
$title = '<strong>Account</strong>';

echo '<h1>' . esc_html(string: $title) . '</h1>';
// <h1>&lt;strong&gt;Account&lt;/strong&gt;</h1>
```

Use [`purify_html()`](purify_html.md) instead when selected rich-text markup should remain functional.
