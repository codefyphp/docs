---
title: throw_if
sidebar_title: throw_if
---

Description
-----------

Throw the given exception if the given condition is true.

Usage
-----

```php
<?php

use function Codefy\Framework\Helpers\throw_if;

function throw_if(
    mixed $condition,
    mixed $exception = RuntimeException::class,
    ...$parameters
): mixed;
```

Parameters
----------

**$condition** (mixed) (required) The truthy statement.

**$exception** (mixed) (optional) An Closure, Exception object, or class string.

**$parameters** (...) (optional) Parameters passed to a Closure or Exception constructor.

Return Value
------------

(mixed) If condition is true, then never, otherwise boolean.

Example
-------

```php
<?php

$auth = gate('edit_user') === false;
throw_if($auth, new AuthException('Access denied.'));
// or
throw_if($auth, AuthException::class, 'Access denied');
```