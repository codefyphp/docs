Description
-----------

Escapes a url.

Usage
-----

    <?php

    use function Qubus\Security\Helpers\esc_url;
    
    esc_url(string $url, array $scheme = ['http', 'https'], bool $encode = false): string;

Parameters
----------

**$url** (string) (required) The url to be escaped.

**$scheme** (array) (optional) An array of acceptable schemes.

**$encode** (bool) (optional) Whether url params should be encoded.

Return Value
------------

(string) The escaped $url after the `esc_url` filter is applied