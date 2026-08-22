---
title: gate
sidebar_title: gate
summary: Retrieve the CodefyPHP authorization Gate or check whether the authenticated user has a named permission with optional rule parameters.
keywords: gate-helper,user-authorization,codefyphp-rbac
---

Description
-----------

Returns a `Codefy\Framework\Auth\Gate` instance or true if user has specified permission.

Usage
-----

```php
<?php

use function Codefy\Framework\Helpers\gate;

function gate(
    ?string $permission = null,
    array $ruleParams = []
): Gate|null|bool;
```

Parameters
----------

**$permission** (string|null) (optional) The permission to check for.

**$rules** (array) (optional) An array of rules for extra checking.

Return Value
------------

(Gate|null|bool) `Gate` instance, null, or true if permission is specified and present.

Example
-------

```php
<?php

use function Codefy\Framework\Helpers\gate;

$auth = gate();
// or
$auth = gate(permission: 'edit_user');
// or
$auth = gate(
    permission: 'edit_user',
    ruleParams: ['userId' => $userId, 'post' => $post]
);
```
