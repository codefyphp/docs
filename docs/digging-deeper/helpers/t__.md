---
title: t__
sidebar_title: t__
---

Description
-----------

Translates a string.

Usage
-----

```php
<?php

use function Qubus\Security\Helpers\t__;

function t__(string $msgid, string $domain = ''): string;
```

Parameters
----------

**$msgid** (string) (required) The string to be translated.

**$domain** (string) (optional) Domain lookup for translated text.

Return Value
------------

(string) Translated text according to current locale.
