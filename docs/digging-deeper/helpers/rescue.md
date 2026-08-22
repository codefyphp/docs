---
title: rescue
sidebar_title: rescue
summary: Run a PHP callback, catch a potential exception, and return a callable or default fallback value with the rescue helper.
keywords: rescue-helper,exception-handling,php-fallback
---

Description
-----------

Catches a potential exception and returns a default value.

Usage
-----

```php
<?php

use Throwable;

use function Qubus\Support\Helpers\rescue;

function rescue(callable $callback, callable|Throwable|bool|null $rescue = null): mixed
```

Parameters
----------

**$callback** (callable) (required) Callback containing the code that might throw an exception.

**$rescue** (callable|Throwable|bool|null) (optional) Fallback to be called when error is thrown.

Return Value
------------

(mixed) The callback if not error is thrown or default value if it's set.

Example
-------

```php
<?php

use Domain\User\Query\FindUserByIdQuery;

use function Codefy\Framework\Helpers\ask;
use function Qubus\Support\Helpers\rescue;

$query = ask(new FindUserByIdQuery(['userId' => '01KFRYX7G3E8PB6QRJ84ZG7J7D']));

// If record exists, you get the result
// If not, the code executes without throwing an error
$user = rescue(function () use($query) {
    return $query;
});

$user = rescue(function () use($query) {
    return $user;
}, null);
```
