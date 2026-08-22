---
title: esc_js
sidebar_title: esc_js
summary: Transport fully constructed inline JavaScript safely through a quoted HTML event attribute with context-aware escaping.
keywords: javascript-escaping,inline-javascript,php-security
description: Escaping for inline JavaScript for echoing JavasScript expressions.
---

Description
-----------

Escaping for inline JavaScript.

Usage
-----

```php
<?php

use function Qubus\Security\Helpers\esc_js;

function esc_js(string $string): string;
```

Parameters
----------

**$string** (string) (required) JavaScript to be escaped.

Return Value
------------

(string) Escaped inline JavaScript after the `esc_js` filter has been applied.

Example
-------

Use it only on fully constructed JavaScript that will be inserted into a quoted HTML event attribute:

```php
use function Qubus\Security\Helpers\esc_js;
use function Qubus\Security\Helpers\esc_js_value;

$handler = 'showMessage(' . esc_js_value(value: $message) . ');';
echo '<button onclick="' . esc_js(string: $handler) . '">Show</button>';
```

It encodes HTML characters such as quotes and angle brackets so the handler cannot escape the onclick="..." attribute.

It does not turn untrusted input into harmless JavaScript:

```php
// Unsafe: attacker input remains JavaScript source code.
echo '<button onclick="' . esc_js(string: $userInput) . '">Run</button>';
```

If `$userInput` is `alert(document.cookie)`, the browser still executes it.

Also, don’t put `esc_js_value()` directly into an HTML attribute:

```php
// Wrong: JSON quotation marks are not HTML-attribute encoded.
echo '<button onclick="' . esc_js_value(value: $input) . '">';
```

The safe order is:

untrusted data

→ esc_js_value()

→ construct trusted handler

→ esc_js()

→ quoted HTML attribute

Whenever possible, avoid inline onclick entirely. Put the value in an escaped data-* attribute and attach an external 
event listener; this works better with strict [Content Security Policy](../../getting-started/security/content-security-policy.md)
