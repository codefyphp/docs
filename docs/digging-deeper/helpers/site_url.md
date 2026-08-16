---
title: site_url
sidebar_title: site_url
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
