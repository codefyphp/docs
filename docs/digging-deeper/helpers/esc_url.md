---
title: esc_url
sidebar_title: esc_url
description: Validates a URL scheme and escapes the URL for a quoted HTML attribute.
---

Description
-----------

Validates a URL scheme and escapes the URL for a quoted HTML attribute. By default, only HTTP and HTTPS URLs are accepted.

Usage
-----

```php
<?php

use function Qubus\Security\Helpers\esc_url;

function esc_url(
    string $url,
    array $scheme = ['http', 'https'],
    bool $encode = false
): string;
```

Parameters
----------

**$url** (string) (required) The url to be escaped.

**$scheme** (array) (optional) An array of acceptable schemes.

**$encode** (bool) (optional) Whether url params should be encoded.

Return Value
------------

(string) The escaped $url after the `esc_url` filter is applied

Example
---------

An invalid URL returns an empty string:

```php
$url = 'https://example.com/search?q=security&sort=newest';

echo '<a href="' . esc_url(url: $url) . '">Search</a>';
// <a href="https://example.com/search?q=security&amp;sort=newest">Search</a>

echo esc_url('javascript:alert(1)');
// ''
```

The optional scheme list restricts the defaults or explicitly enables a non-active scheme:

```php
$downloadUrl = esc_url(url: 'ftp://downloads.example.com/file.zip', scheme: ['https', 'ftp']);
```

Active and local schemes such as `javascript`, `data`, and `file` remain blocked even if supplied in the scheme list. 
`esc_url()` does not enforce a trusted hostname, prevent open redirects, or protect against server-side request 
forgery; apply those policies separately.

The third `$encode` argument is retained for backwards compatibility and applies RFC 3986 normalization to the URL 
fragment when `true`.
