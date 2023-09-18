Description
-----------

Escapes a translated string to make it safe for HTML attribute.

Usage
-----

    use function Qubus\Security\Helpers\esc_attr__;
    
    esc_attr__(string $string, string $domain = 'qubus'): string;

Parameters
----------

**$string** (string) (required) String to translate and escape.

**$domain** (string) (optional) Unique identifier for retrieving a translated string.

Return Value
------------

(string) Translated and escaped string.