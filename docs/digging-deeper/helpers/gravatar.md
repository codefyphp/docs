---
title: gravatar
sidebar_title: gravatar
---

Description
-----------

Return a new Gravatar Image instance.

Usage
-----

```php
<?php

use Gravatar\Image;

use function Codefy\Framework\Helpers\gravatar;

function gravatar(?string $email = null): Image;
```

Parameters
----------

**$email** (string|null) (optional) The email address to use for the Gravatar.

Return Value
------------

(Image) Will return an `Image` instance.

Example
-------

```php
<?php

// Get a Gravatar image instance:
$image = gravatar('email@example.com');
// return: Gravatar\Image

// Get a Gravatar image URL:
$imageUrl = gravatar('email@example.com')->url();
// return: //www.gravatar.com/avatar/5658ffccee7f0ebfda2b226238b1eb6e

// Show a Gravatar image URL:
echo gravatar('email@example.com');
// output: //www.gravatar.com/avatar/5658ffccee7f0ebfda2b226238b1eb6e

// With optional parameters:
$avatar = gravatar('email@example.com')
    ->size(120)
    ->defaultImage('robohash')
    ->maxRating('pg')
    ->extension('jpg');
echo $avatar;

// Or set the email later:
$avatar = gravatar()
    ->email('email@example.com')
    ->size(200);
echo $avatar;

// With initials (convenience method):
$avatar = gravatar('email@example.com')
    ->withInitials('JD')
    ->size(120);
echo $avatar;
```