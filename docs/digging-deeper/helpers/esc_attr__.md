---
title: esc_attr__
sidebar_title: esc_attr__
---

Description
-----------

Escapes a translated string to make it safe for HTML attribute.

Usage
-----

```php
<?php

use function Qubus\Security\Helpers\esc_attr__;

function esc_attr__(string $string, string $domain = 'qubus'): string;
```

Parameters
----------

**$string** (string) (required) String to translate and escape.

**$domain** (string) (optional) Unique identifier for retrieving a translated string.

Return Value
------------

(string) Translated and escaped string.

Example
--------

```php
use function Qubus\Security\Helpers\esc_attr__;

echo '<button aria-label="' . esc_attr__(string: 'Close dialog', domain: 'application') . '">×</button>';
```
