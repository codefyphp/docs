---
title: site_url
sidebar_title: site_url
summary: Generate the CodefyPHP application base URL with an optional relative path and a normalized trailing slash using site_url.
keywords: site-url,url-generation,codefyphp-helper
---


Description
-----------

Returns the url of your application.

Usage
-----

```php
<?php

use function Codefy\Framework\Helpers\site_url;

function site_url(string $path = ''): string;
```

Parameters
----------

**$path** (string) (optional) Relative path appended to base url.

Return Value
------------

(string) Url with trailing slash.
