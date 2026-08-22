---
title: purify_html
sidebar_title: purify_html
summary: Sanitize untrusted rich-text HTML for safe document-body output by removing executable markup, unsafe attributes, and dangerous URL schemes.
keywords: html-purifier,xss-prevention,php-security
description: Accepts untrusted rich-text HTML and returns a safe HTML fragment for an HTML document body.
---

Description
-----------

Accepts untrusted rich-text HTML and returns a safe HTML fragment for an HTML document body. It
preserves common formatting while removing executable markup, unsafe attributes, and dangerous URL schemes.

This function should only be used on output. Except uploading images, never use this function on input. 
All inputted data should be accepted and then purified on output for optimal results. For output of images, make sure 
to escape with [`esc_url()`](esc_url.md).

Usage
-----

```php
<?php

use Qubus\Security\HtmlPurifier;

use function Qubus\Security\Helpers\purify_html;

function purify_html(string|array|null $string = null, bool $isImage = false): HtmlPurifier|string|bool|array;
```

Parameters
----------

**$string** (string|array|null) (required) Output to purify.

**$isImage** (bool) (optional) Whether the output is an image.

Return Value
------------

(string) The purified output.

Example
---------

Purify as late as possible, immediately before rendering:

```php
<?php

use function Qubus\Security\Helpers\purify_html;

$untrustedHtml = <<<'HTML'
<p class="intro" onclick="alert(1)">
    Hello <strong>world</strong>.
    <a href="javascript:alert(1)" target="_blank">Open</a>
</p>
HTML;

$safeHtml = purify_html(string: $untrustedHtml);

echo $safeHtml;
```

The resulting fragment is equivalent to:

```html
<p class="intro">
    Hello <strong>world</strong>.
    <a target="_blank" rel="noopener noreferrer">Open</a>
</p>
```

The event handler and active link URL are removed. Links using `target="_blank"` receive `noopener noreferrer` to 
prevent reverse-tabnabbing.

### What it protects against

The purifier performs compatibility normalization and then parses the fragment with PHP's HTML5 parser. The parsed 
document is filtered using element, attribute, and URI-scheme allow lists before being serialized again. 
This protects against:

- malformed-markup and parser-confusion attacks;
- scripts, iframes, templates, objects, SVG, MathML, and other active content;
- inline event handlers, CSS, `srcdoc`, `srcset`, XML namespaces, and form actions;
- entity, control-character, and repeatedly percent-encoded URI schemes;
- `javascript:`, `data:`, `blob:`, `file:`, and `vbscript:` URLs.

Unknown non-active elements are unwrapped so their safe child content remains. Raw-text and embedded active 
elements are removed. Inline `style` attributes are intentionally not retained.

Safe absolute and relative links are supported, including HTTPS, mail, and telephone links:

```php
use function Qubus\Security\Helpers\purify_html;

$purifier = purify_html();

echo $purifier->purify(string: '<a href="https://example.com/docs">Documentation</a>');
echo $purifier->purify(string: '<a href="/account">Account</a>');
echo $purifier->purify(string: '<a href="mailto:help@example.com">Email support</a>');
echo $purifier->purify(string: '<a href="tel:+15551234567">Call support</a>');
```

HTTP and HTTPS image sources are also retained. Remote images can still disclose a visitor's IP address and request 
metadata, so proxy or disable user-supplied images when that privacy boundary matters.

### Custom allow lists

The safe element, attribute, and URI-scheme lists are public configuration properties:

```php
use function Qubus\Security\Helpers\purify_html;

$purifier = purify_html();

$purifier->allowedHtmlElements[] = 'footer';
$purifier->allowedHtmlAttributes[] = 'itemprop';
$purifier->allowedUriSchemes[] = 'ftp';

echo $purifier->purify(string: $untrustedHtml);
```

Treat these lists as trusted application configuration, never user input. Inherently active content remains 
blocked even if `script`, `style`, or `javascript` is added to a public allow list.

The legacy public properties—including the intentionally preserved misspelling `xssDisalowedAttibutes`—remain 
available for backwards compatibility. Prefer the explicit allow-list properties in new code.

### Arrays and image-check compatibility mode

An array of HTML strings can be purified without losing its keys:

```php
$safe = $purifier->purify([
    'summary' => '<p>Short summary</p>',
    'body' => $submittedBody,
]);
```

Passing `true` as the second argument enables the legacy image-check mode. It returns a boolean indicating whether 
purification would alter the supplied string, including for every value in an input array:

```php
$checks = $purifier->purify([
    'safe' => 'plain metadata',
    'unsafe' => '<?php echo 1; ?>',
], true);

// ['safe' => true, 'unsafe' => false]
```

This mode does not prove that uploaded bytes are a valid or harmless image. Validate uploads separately with `finfo`, 
an image decoder, size limits, generated storage names, and storage outside the executable web root.

### Filename sanitization

`sanitizeFilename()` removes control characters, directory traversal, path separators, and encoded path variants:

```php
$filename = $purifier->sanitizeFilename(string: '../../avatar.php');
// avatar.php

$relative = $purifier->sanitizeFilename(string: '../approved/images/avatar.jpg', true);
// approved/images/avatar.jpg
```

The relative-path option preserves approved `/` separators but still removes absolute and parent-directory traversal. 
Filename sanitization is not path authorization: always resolve files beneath a trusted base directory and 
enforce upload type, extension, and overwrite rules separately.

### Output-context rules

Purified output is intended only as an HTML fragment in element content:

```php
<article><?= $purifier->purify(string: $submittedBody) ?></article>
```

Do not reuse that output in an HTML attribute, URL, JavaScript, CSS, SQL, or shell command. Those contexts 
require their own validation and escaping. A restrictive Content Security Policy remains useful defense in depth.
