---
title: abort_if
sidebar_title: abort_if
summary: Conditionally throw a CodefyPHP HttpException when a boolean expression is true, with a status code, optional URI, and custom message.
keywords: abort-if,http-exception,php-helper
---

Description
-----------

Abort (throw an HttpException) if the given condition is true.

Usage
-----

```php
<?php

use function Codefy\Framework\Helpers\abort_if;

function abort_if(
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

use Domain\User\Query\FindUserByIdQuery;

use function Codefy\Framework\Helpers\abort_if;
use function Codefy\Framework\Helpers\ask;

function find_user_by_id(string $id): object|bool
{
    return ask(new FindUserByIdQuery(['userId' => $id]));
}

abort_if(
    condition: false === find_user_by_id('01KDNPDG0YE32R47FBC6R0VBE2'),
    code: 404,
    uri: '/admin/',
    message: 'User not found.'
);
```
