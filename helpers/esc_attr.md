Description
-----------

Escaping for html attributes.

Usage
-----

    use function Qubus\Security\Helpers\esc_attr;
    
    esc_attr(string $string): string;

Parameters
----------

**$string** (string) (required) Attribute to be escaped.

Return Value
------------

(string) Escaped HTML attribute after the `esc_attr` filter has been applied.