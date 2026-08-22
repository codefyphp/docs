---
title: method_field
sidebar_title: method_field
summary: Generate a hidden HTML form input that spoofs PUT, PATCH, DELETE, or another HTTP method for CodefyPHP route handling.
keywords: method-field,http-method-override,html-forms
---

Description
-----------

This function generates an HTML hidden input field containing the spoofed value of the form's HTTP verb.

Usage
-----

```php
<?php

use Qubus\Support\HtmlString;

use function Codefy\Framework\Helpers\method_field;

function method_field(string $method): HtmlString;
```

Parameters
----------

**$method** (string) (required) Spoofed value.

Return Value
------------

(string) The hidden input field.

Example
-------

```php
<form method="POST">
    <?=\Codefy\Framework\Helpers\method_field('put');?>
</form>
```

Result
-------

```html
<form method="POST">
    <input type="hidden" name="_method" value="PUT" />
</form>
```
