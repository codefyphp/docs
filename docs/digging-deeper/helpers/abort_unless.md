---
title: abort_unless
sidebar_title: abort_unless
summary: Conditionally throw a CodefyPHP HttpException unless a boolean expression is true, with a status code, optional URI, and custom message.
keywords: abort-unless,http-exception,php-helper
---

Description
-----------

Abort (throw an HttpException) unless the given condition is true.

Usage
-----

```php
<?php

use function Codefy\Framework\Helpers\abort_if;

function abort_unless(
    bool $condition,
    int $code,
    ?string $uri = null,
    string $message = ''
): void;
```

Parameters
----------

**$condition** (bool) (required) The Exception code that evaluates to an HTTP status code.

**$code** (int) (required) The Exception code that evaluates to an HTTP status code.

**$uri** (string|null) (optional) Redirect uri.

**$message** (string) (optional) The exception message to throw.

Return Value
------------

(void) Returns void.

Example
-------

```php
<?php

use function Codefy\Framework\Helpers\abort_if;
use function Codefy\Framework\Helpers\gate;

abort_unless(
    condition: gate('edit_user'),
    code: 403,
    uri: '/admin/',
    message: 'Access denied.'
);
```
