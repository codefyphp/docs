---
title: gate
sidebar_title: gate
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
