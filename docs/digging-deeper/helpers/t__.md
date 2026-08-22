---
title: t__
sidebar_title: t__
summary: Translate a message into the active application locale with an optional Gettext text domain using the Qubus t__ helper.
keywords: php-translation,gettext,localization-helper
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
