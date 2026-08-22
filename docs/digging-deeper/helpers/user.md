---
title: user
sidebar_title: user
summary: Retrieve the currently authenticated CodefyPHP user as an object, boolean, or null with the user convenience helper.
keywords: authenticated-user,user-helper,codefyphp-auth
---

Description
-----------

Returns the authenticated user.

Usage
-----

```php
<?php

use function Codefy\Framework\Helpers\user;

function user(): object|bool|null;
```

Return Value
------------

(object|null|bool) Returns an object of user data, bool, or null.

Example
-------

```php
<?php

use function Codefy\Framework\Helpers\user;

$user = user();
echo $user->user_id; // returns the user's ID
echo $user->email; // returns the user's email
```
