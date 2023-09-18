Description
-----------

Escaping for inline javascript.

Usage
-----

    use function Qubus\Security\Helpers\esc_js;
    
    esc_js(string $string): string;

Parameters
----------

**$string** (string) (required) Javascript to be escaped.

Return Value
------------

(string) Escaped inline javascript after the `esc_js` filter has been applied.

Example
-------

    $esc_js = json_encode("Joshua's \"code\"");
    $attribute = esc_js("alert($esc_js);");
    echo '<input type="button" value="push" onclick="'.$attribute.'" />';