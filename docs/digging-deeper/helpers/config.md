---
title: config
sidebar_title: config
summary: Read and set CodefyPHP configuration values with dot notation, retrieve the ConfigContainer, and supply defaults for missing options.
keywords: config-helper,codefyphp-configuration,dot-notation
---


Description
-----------

Return the `ConfigContainer` instance or get / set the specified configuration value. The configuration values may be 
accessed using "dot" syntax, which includes the name of the file and the option you wish to access. You may also 
provide a default value that will be returned if the configuration option does not exist

Usage
-----

```php
<?php

use function Codefy\Framework\Helpers\config;

function config(string|array|null $key = null, mixed $default = ''): mixed;
```

Parameters
----------

**$key** (string|array|null) (required) Query to pass through the query bus.

**$default** (mixed) (optional) Default value.

## Examples

```php
<?php

use function Codefy\Framework\Helpers\config;

$timezone = config(key: 'app.timezone');
// or
$timezone = config(key: 'app.timezone', default: 'America/Los_Angeles');
```

```php
<?php

use function Codefy\Framework\Helpers\config;

$config = config(); // returns the ConfigContainer instance.
```

```php
<?php

use function Codefy\Framework\Helpers\config;

config(key: ['app' => ['locale' => 'es']]); // set app.locale value to 'es'.
```
