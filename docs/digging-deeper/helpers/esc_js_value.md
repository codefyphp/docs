---
title: esc_js_value
sidebar_title: esc_js_value
summary: Serialize untrusted PHP data into a safe JavaScript expression for inline scripts and event handlers with esc_js_value.
keywords: javascript-values,xss-prevention,php-security
description: Secures untrusted data for JavaScript syntax.
---

Description
-----------

`esc_js_value()` secures untrusted data for JavaScript syntax while [`esc_js()`](esc_js.md) transports already-constructed 
JavaScript through an HTML attribute. They solve different encoding layers and can be used together.

Usage
-----

```php
<?php

use function Qubus\Security\Helpers\esc_js_value;

function esc_js_value(mixed $value): string;
```

Parameters
----------

**$string** (string) (required) Untrusted JavaScript that is serialized.

Return Value
------------

(string) Returns a safe expression.

Example
-------

When an inline event attribute is unavoidable:

```php
<?php

use function Qubus\Security\Helpers\esc_js;
use function Qubus\Security\Helpers\esc_js_value;

require 'vendor/autoload.php';

$message = "Joshua's \"code\"";

// First: serialize untrusted data as a JavaScript value.
$handler = 'alert(' . esc_js_value(value: $message) . ');';

// Second: escape the complete handler for its HTML attribute.
$attribute = esc_js(string: $handler);

echo '<input type="button" value="push" onclick="' . $attribute . '" />';
```

Use it for data, not JavaScript source code.

`$value = esc_js_value(value: $userInput);`

For a string, it returns a complete quoted JavaScript expression:

`Joshua's "code"`

becomes approximately:

`"Joshua\u0027s \u0022code\u0022"`

It also safely serializes arrays, numbers, booleans, and null:

`esc_js_value(value: ['name' => $userName, 'admin' => false]);`

It can be inserted directly as an expression in a script block:

```javascript
<script>
const user = <?= esc_js_value(value: $userData) ?>;
</script>
```

Do not add another pair of JavaScript quotes because `esc_js_value()` already supplies them for strings:

```php
// Wrong
const value = '<?= esc_js_value(value: $input) ?>';

// Correct
const value = <?= esc_js_value(value: $input) ?>;
