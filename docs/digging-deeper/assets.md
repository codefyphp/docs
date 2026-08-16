---
title: Asset Management
sidebar_title: Asset Management
order: 35
---

The `Codefy\Framework\Support\Assets` class is a simple asset management for CodefyPHP.

## Usage

### View/Layouts

You can use the global property to instantiate the `Assets` class:

```php
<?php

$assets = Codefy\Framework\Proxy\Codefy::$PHP->assets;
```

To generate the CSS `<link rel="stylesheet">` tags:

```php
<?php

echo $assets->css();
```

To generate the JavaScript `<script>` tags:

```php
<?php

echo $assets->js();
```

### Routes/Controllers

Basically, to add an asset, no matter if it's CSS or JS or a collection of both, is:

```php
<?php

$assets->add('filename');
```

!!! note
    For more advanced uses, keep reading but please note that there are other methods not documented here. For a full 
    list of all the available methods please check out the [api](../api/Qubus/Support/Assets.md).

Add more than one asset at once:

```php
<?php

$assets->add(['another/file.js', 'one/more.css']);
```

Add an asset from a local package:

```php
<?php

$assets->add('twitter/bootstrap:bootstrap.min.css');
```

Not all local asset filenames are considered to be relative to you assets directory (configurable via `css_dir` and 
`js_dir` options) so you don't need to provide it every time with `js/file.js` or `css/file.css`, using just `file.js` or 
`file.css` will be enough.

You may add remote assets in the same fashion:

```php
<?php

$assets->add('//cdn.example.com/jquery.js');
$assets->add('http://example.com/style.css');
```

If your assets have no extension and autodetection fail, you can use canonical functions 
_(they accept an array of assets as well)_:

```php
<?php

$assets->addCss('CSSfile.foo');
$assets->addJs('JavaScriptFile.bar');
```

If at some point you decide you added the wrong assets you can reset them and start over:

```php
<?php

$assets->reset();    // Reset both CSS and JS
$assets->resetCss(); // Reset only CSS
$assets->resetJs();  // Reset only JS
```

All methods that don't generate output will accept chaining:

```php
<?php

$assets->reset()->add('collection')->addJs('file.js')->css();
```

## Configuration

Asset directories and other options are configurable via `./config/assets.php`.

### Collections

A collection is a named set of assets, that is, a set of JavaScript and CSS files. Any collection may include 
more collections, allowing dependency definition and collection nesting. Collections can be created on runtime or 
via config file.

To register a collection on runtime for later use:

```php
<?php

$assets->registerCollection($collectionName, ['some', 'awesome', 'assets']);
```

To preconfigure collections using the config file:

```php
<?php

// ... File: config/assets.php ...
'collections' => [
    'one'	=> 'one.css',
    'two'	=> ['two.css', 'two.js'],
    'external'	=> ['http://example.com/external.css', 'https://secure.example.com/https.css', '//example.com/protocol/agnostic.js'],
    'mix'	=> ['internal.css', 'http://example.com/external.js'],
    'nested' => ['one', 'two'],
    'duplicated' => ['nested', 'one.css','two.css', 'three.js'],
],
```

After setup, you can use the above collection in different scenarios:

Using `$assets->add('two');` will result in

```html
<!-- CSS -->
<link type="text/css" rel="stylesheet" href="css/two.css" />
<!-- JS -->
<script type="text/javascript" src="js/two.js"></script>
```

Using `$assets->add('external');` will result in

```html
<!-- CSS -->
<link type="text/css" rel="stylesheet" href="http://example.com/external.css" />
<link type="text/css" rel="stylesheet" href="https://secure.example.com/https.css" />
<!-- JS -->
<script type="text/javascript" src="//example.com/protocol/agnostic.js"></script>
```

Using `$assets->add('mix');` will result in

```html
<!-- CSS -->
<link type="text/css" rel="stylesheet" href="css/internal.css" />
<!-- JS -->
<script type="text/javascript" src="http://example.com/external.js"></script>
```

Using `$assets->add('nested');` will result in

```html
<!-- CSS -->
<link type="text/css" rel="stylesheet" href="css/one.css" />
<link type="text/css" rel="stylesheet" href="css/two.css" />
<!-- JS -->
<script type="text/javascript" src="js/two.js"></script>
```

Using `$assets->add('duplicated');` will result in

```html
<!-- CSS -->
<link type="text/css" rel="stylesheet" href="css/one.css" />
<link type="text/css" rel="stylesheet" href="css/two.css" />
<!-- JS -->
<script type="text/javascript" src="js/two.js"></script>
<script type="text/javascript" src="js/three.js"></script>
```

!!! note
    The last collection has duplicated assets that are only included once.

### Pipeline

To enable pipeline use the `pipeline` config option:

```php
<?php

'pipeline' => true,
```

Once it's enabled, all your assets will get concatenated and minified to a single file, improving load speed and 
reducing the number of requests that a browser makes to render a web page.

This process can take a few seconds depending on the amount of assets and your connection, but it's triggered only 
the first time you load a page whose assets have never been pipelined before. The subsequent times the same page 
(or any page using the same assets) is loaded, the previously pipelined file will be used giving you much faster 
loading time and less bandwidth usage.

!!! note
    For obvious reasons, enabling `pipeline` is recommended only for production environment.

If your assets have changed since they were pipelined, use the provided `codex` command to purge the pipeline cache:

```shell
php codex asset:flush
```

Alternatively, you can set the `pipeline` config option to a string value that evaluates to `true`. That value will be 
used as the salt of the pipeline hash. If you use `auto` as the value, the salt will be automatically calculated 
based on your assets last modification time.

**Example:**

```php
<?php

'pipeline' => 'version 1.0',
```

Finally, if you happen to use NGINX with the [gzip_static](https://nginx.org/en/docs/http/ngx_http_gzip_static_module.html) 
feature enabled, add the following config option to automatically create a suitable `gziped` version of the 
pipelined assets:

```php
<?php

'pipeline_gzip' => true,
```

### Other Options

* `'autoload' => [],` = Here you may set which assets (CSS files, JavaScript files or collections) should be loaded by default.
* `'css_dir' => 'css',` = Override default relative path for css assets.
* `'js_dir' => 'js'`, = Override default relative path for js assets.
* `'pipeline_dir' => 'min',` = Override default folder for pipelined assets.

It is possible to **change any config option on the fly** by passing an array of settings to the `config()` method. 
Useful if some assets use a different base directory or if you want to pipeline some assets and skip others from the 
pipeline:

```php
<?php

echo $assets->reset()->add('do-not-pipeline-this.js')->js();
echo $assets->reset()->add('please-pipeline-this.js')->config(['pipeline' => true])->js();
```

### Multitenancy

Multitenancy is achieved using `groups`. A `group` is an isolated container of the library. Each group is independent 
of other groups so it uses its own settings and asset flow. This is useful if you need different approaches for 
different types of assets (for instance, you may need some assets to be pipelined but not others). Therefore, when 
using multiple groups, it is your responsibility to make sure the assets of different groups that depend on each other 
are loaded in their right order.

By default, if no groups are defined the default group is used. To define a group, just nest your normal settings 
within an array in the config file. The array key will be the group name. For instance:

```php
<?php

// ... File: config/assets.php ...

// Default group
'default' => [
    'pipeline' => true,
    'js_dir' => 'js',
    // ... more options for default group
],

// Other group
'group1' => [
    'pipeline' => false,
    'public_dir' => '/foo',
    // ... more options for group1
],

// Another group
'group2' => [
    'pipeline' => false,
    'css_dir' => 'css/admin',
    // ... more options for group2
],
```

When choosing which group you want to interact with, use the `group()` method. If no group is specified the 'default' 
group will be used.

```php
<?php

$assets->add('foo.js')->js(); // Uses default group
$assets->group('group1')->add('bar.css')->css(); // Uses the 'group1' group.
```





