---
title: php_where
sidebar_title: php_where
summary: Evaluate SQL WHERE-style comparisons in PHP with a key, operator, and comparison value using the php_where helper.
keywords: php-where,conditional-filtering,php-helper
---

Description
-----------

SQL Where operator in PHP.

Usage
-----

```php
<?php

use function Qubus\Support\Helpers\php_where;

function php_where(string $key, string $operator, mixed $pattern): bool;
```

Parameters
----------

**$key** (string) (required) Term to search.

**$operator** (string) (required) The filter to perform.

**$pattern** (mixed) (required) Term to check against.

Return Value
------------

(bool) Will return `true` if condition matches, `false` otherwise.

Example
-------

```php
<?php

// Where dog is in ['cat', 'bear', 'chicken', 'dog']
php_where('dog', 'in', ['cat', 'bear', 'chicken', 'dog']); // true
```
