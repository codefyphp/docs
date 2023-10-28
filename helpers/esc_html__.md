Description
-----------

Escapes a translated string to make it safe for HTML output.

Usage
-----

    <?php

    use function Qubus\Security\Helpers\esc_html__;
    
    esc_html__(string $string, string $domain = 'qubus'): string;

Parameters
----------

**$string** (string) (required) String to translate.

**$string** (string) (optional) Text domain.

Return Value
------------

(string) Translated string.