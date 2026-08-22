---
title: esc_html__
sidebar_title: esc_html__
summary: Translate a string and escape it for safe plain-text output between HTML tags with the Qubus esc_html__ helper.
keywords: translated-html,html-escaping,php-i18n
---

Description
-----------

Escapes a translated string to make it safe for HTML output.

Usage
-----

```php
<?php

use function Qubus\Security\Helpers\esc_html__;

function esc_html__(string $string, string $domain = 'qubus'): string;
```

Parameters
----------

**$string** (string) (required) String to translate.

**$string** (string) (optional) Text domain.

Return Value
------------

(string) Translated string.

Example
--------

```php
use function Qubus\Security\Helpers\esc_html__;

echo '<h2>' . esc_html__(string: 'Account settings', domain: 'application') . '</h2>';
```
