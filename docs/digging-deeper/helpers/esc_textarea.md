---
title: esc_textarea
sidebar_title: esc_textarea
---

Description
-----------

Escapes text placed between `<textarea>` tags. This helper is for the textarea body. Escape values in attributes 
such as `name`, `class`, or `data-*` with `esc_attr()`.

Usage
-----

```php
<?php

use function Qubus\Security\Helpers\esc_textarea;

function esc_textarea(string $string): string;
```

Parameters
----------

**$string** (string) (required) String to escape.

Return Value
------------

(string) Escaped string.
