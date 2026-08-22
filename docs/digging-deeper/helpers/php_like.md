---
title: php_like
sidebar_title: php_like
summary: Match a PHP string against a SQL LIKE-style pattern with percent wildcards and return whether the subject satisfies the search expression.
keywords: php-like,pattern-matching,string-search
---

Description
-----------

SQL Like operator in PHP.

Usage
-----

```php
<?php

use function Qubus\Support\Helpers\php_like;

function php_like(string $pattern, string $subject): bool;
```

Parameters
----------

**$pattern** (string) (required) Search term.

**$subject** (string) (required) The text to search for.

Return Value
------------

(bool) Will return `true` if found, `false` otherwise.

Example
-------

```php
<?php

php_like('%uc%','Lucy'); //true

php_like('%cy', 'Lucy'); //true

php_like('lu%', 'Lucy'); //true

php_like('%lu', 'Lucy'); //false

php_like('cy%', 'Lucy'); //false
```
