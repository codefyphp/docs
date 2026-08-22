---
title: is_error
sidebar_title: is_error
summary: Check whether a PHP value is a Qubus Error instance and branch safely between successful results and application errors.
keywords: is-error,error-checking,php-helper
---

Description
-----------

Check whether variable is an Error instance.

Usage
-----

```php
<?php

use function Qubus\Error\Helpers\is_error;

function is_error(mixed $object): bool;
```

Parameters
----------

**$object** (mixed) The object to check.

Return Value
------------

(bool) True if an Error instance, false otherwise.

Example
-------

```php
<?php

use Qubus\Error\Error;

use function Qubus\Error\Helpers\is_error;

function has_permission(string $permission): Error|string
{
    if ($permission === '') {
        return new Error('The permission value is invalid');
    }
    
    return $permission;
}

$permission = has_permission('');

if (is_error($permission)) {
    echo $permission->getMessage();
}
```
