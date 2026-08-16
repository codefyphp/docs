---
title: gravatar_profile
sidebar_title: gravatar_profile
---

Description
-----------

Return a new Gravatar Profile instance.

Usage
-----

```php
<?php

use Gravatar\Profile;

use function Codefy\Framework\Helpers\gravatar_profile;

function gravatar_profile(?string $email = null): Profile;
```

Parameters
----------

**$email** (string|null) (optional) The email address to use for the Gravatar.

Return Value
------------

(Profile) Will return a `Profile` instance.

Example
-------

```php
<?php

// Get a Gravatar profile instance:
$profile = gravatar_profile('email@example.com');
// return: Gravatar\Profile

// Get a Gravatar profile URL:
echo gravatar_profile('email@example.com');
// output: https//www.gravatar.com/5658ffccee7f0ebfda2b226238b1eb6e

// With format parameter:
$profileUrl = gravatar_profile('email@example.com')
    ->format('json')
    ->url();
```
