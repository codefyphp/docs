---
title: abort
sidebar_title: abort
summary: Use the CodefyPHP abort helper to stop request processing by throwing an HttpException with a status code, redirect URI, message, and previous exception.
keywords: abort-helper,http-exception,codefyphp
---

Description
-----------

Throw an HttpException with the given data.

Usage
-----

```php
<?php

use Throwable;

use function Codefy\Framework\Helpers\abort;

function abort(
    int $code = 500,
    ?string $uri = null,
    string $message = '',
    ?Throwable $previous = null
): never;
```

Parameters
----------

**$code** (int) (optional) The Exception code that evaluates to an HTTP status code.

**$uri** (string|null) (optional) Redirect uri.

**$message** (string) (optional) The exception message to throw.

**$previous** (Throwable|null) (optional) The previous exception used for the exception chaining.

Return Value
------------

(never) Should never return a value.

Example
-------

```php
<?php

use Domain\User\Query\FindUserByIdQuery;

use function Codefy\Framework\Helpers\abort;
use function Codefy\Framework\Helpers\ask;

function find_user_by_id(string $id): object
{
    $user = ask(new FindUserByIdQuery(['userId' => $id]));

    if (!$user) {
        abort(
            code: 404,
            uri: '/admin/',
            message: 'User not found.'
        );
    }

    return $user;
}
```
